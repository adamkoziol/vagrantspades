Vagrant.configure("2") do |config|
	# Defines the devEnv virtual machine
	config.vm.define "devEnv" do |a|
		# Set the provider as docker
		a.vm.provider "docker" do |d|
			# Set the image to use here
			d.image = "olcbioinformatics/vagrantspades"
			# These arguments will be added to the docker run command
			d.create_args = ["-it", "--name", "spades_env"]
			# Keeps the docker container running
			d.remains_running = true
			# Informs vagrant that the docker container has ssh
			d.has_ssh = true
			# STILL TO BE TESTED
			# When this is run on a Mac or Windows machine, vagrant will spin up a virtual environment that supports docker
			d.vagrant_machine = "dockerhost"
    			d.vagrant_vagrantfile = "./DockerHostVagrantfile"
		end
		# These credentials must match those specified in the docker image
		a.ssh.username = "root"
		# Input the provided password
		a.ssh.password = "biohazard"
	end
end
