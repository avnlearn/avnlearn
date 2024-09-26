# Step 1: Install VirtualBox

1. **Update your system**:

   ```bash
   sudo pacman -Syu
   ```

2. **Install VirtualBox**:

   ```bash
   sudo pacman -S virtualbox
   ```

3. **[Optional] Install Extension pack** : [VirtualBox Extension Pack](https://www.virtualbox.org/wiki/Downloads) or [Preview VirtualBox Extension Pack](https://www.virtualbox.org/wiki/Download_Old_Builds)

   ```bash
   VBoxManage extpack install Oracle_*_VirtualBox_Extension_Pack-version.vbox-extpack
   ```

4. **Load the VirtualBox kernel modules** (if not already loaded):

   ```bash
   sudo modprobe vboxdrv
   ```

   **[Optional]**

   ```bash
   sudo modprobe vboxnetadp
   sudo modprobe vboxnetflt
   sudo modprobe vboxpci
   ```

   To ensure these modules load automatically on boot, you can add them to the /etc/modules-load.d/virtualbox.conf file:

   ```bash
   echo -e "vboxdrv\nvboxnetadp\nvboxnetflt\nvboxpci" | sudo tee /etc/modules-load.d/virtualbox.conf
   ```

5. **Add Your User to the vboxusers Group**
   To allow your user to run VirtualBox, you need to add your user to the vboxusers group:

   ```bash
   sudo usermod -aG vboxusers $(whoami)
   ```

   After running this command, log out and log back in for the changes to take effect.

# Step 2: Install Vagrant

```bash
sudo pacman -S vagrant
```

## **[Optional] Install Vagrant Plugin**

```bash
vagrant plugin install vagrant-vbguest vagrant-share
```

## Step 2.1: Create a Vagrant Project

1. **Create a new directory for your Vagrant project**:

   ```bash
   mkdir ~/vagrant-wordpress
   cd ~/vagrant-wordpress
   ```

2. **Initialize a new Vagrantfile**:
   ```bash
   vagrant init
   ```

## Step 2.2: Configure the Vagrantfile

Open the `Vagrantfile` in a text editor and modify it to set up a LAMP stack (Linux, Apache, MySQL, PHP) for WordPress. Here’s a basic example:

```ruby
config.vm.synced_folder '/host/path', '/guest/path', SharedFoldersEnableSymlinksCreate: false
```

```ruby
Vagrant.configure("2") do |config|
#   config.vm.box = "avnlearn-site"
  # Use the official Ubuntu box
  config.vm.box = "ubuntu/bionic64"
  # Using NFS for better performance
#   config.vm.synced_folder "./site", "/var/www/html", type: "nfs"
  # Forward ports
  config.vm.network "forwarded_port", guest: 80, host: 8080
  # Shared Folders
  config.vm.synced_folder './site', '/home', SharedFoldersEnableSymlinksCreate: false
  # Provisioning with shell script
  config.vm.provision "shell", inline: <<-SHELL
    # Update and install necessary packages
    apt-get update
    apt-get install -y apache2 mysql-server php php-mysql libapache2-mod-php

    # Enable Apache mod_rewrite
    a2enmod rewrite
    systemctl restart apache2

    # Download and set up WordPress
    ls /var/www/html
    cd /var/www/html
    wget https://wordpress.org/latest.tar.gz
    tar -xvzf latest.tar.gz
    mv wordpress/* ./
    rm -rf wordpress latest.tar.gz

    # Set permissions
    chown -R www-data:www-data /var/www/html
    chmod -R 755 /var/www/html

    # Create a MySQL database for WordPress
    service mysql start
    mysql -e "CREATE DATABASE u591392136_RZ4e8;"
    mysql -e "CREATE USER 'u591392136_aj32K'@'localhost' IDENTIFIED BY '3qbP43IaDH';"
    mysql -e "GRANT ALL PRIVILEGES ON u591392136_RZ4e8.* TO 'u591392136_aj32K'@'localhost';"
    mysql -e "FLUSH PRIVILEGES;"
  SHELL
end
```

## Step 2.3: Start the Vagrant Environment

1. **Start the Vagrant box**:

   ```bash
   vagrant up
   ```

2. **SSH into the Vagrant box**:
   ```bash
   vagrant ssh
   ```

### [Optional Alread] Step 2.4: Set Up MySQL Database for WordPress

1. **Log into MySQL**:

   ```bash
   sudo mysql -u root
   ```

2. **Create a database and user for WordPress**:
   ```sql
   CREATE DATABASE wordpress;
   CREATE USER 'wpuser'@'localhost' IDENTIFIED BY 'password';
   GRANT ALL PRIVILEGES ON wordpress.* TO 'wpuser'@'localhost';
   FLUSH PRIVILEGES;
   EXIT;
   ```

### Step 2.5: Complete WordPress Installation

1. **Open your web browser** and go to `http://localhost:8080`.
2. **Follow the WordPress installation steps**, using the database name `wordpress`, username `wpuser`, and the password you set.

### Step 2.6: Manage Your Vagrant Environment

- To stop the Vagrant box:

  ```bash
  vagrant halt
  ```

- To destroy the Vagrant box (removes all data):
  ```bash
  vagrant destroy
  ```
