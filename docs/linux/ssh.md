
# SSH Command Line Cheatsheet

## Basics

- **Connect to Server**

  ```bash
  ssh user@host
  ```

- **Specify Port**

  ```bash
  ssh -p port_number user@host
  ```

- **Connect with Identity File**

  ```bash
  ssh -i /path/to/private_key user@host
  ```

- **Connect Using a Config File**

  ```bash
  ssh host_alias
  ```

  *Config file path: `~/.ssh/config`*

  ```plaintext
  Host host_alias
      HostName hostname
      User username
      Port port_number
      IdentityFile /path/to/private_key
  ```

## Key Management

- **Generate SSH Key Pair**

  ```bash
  ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
  ```

- **Copy Public Key to Server**

  ```bash
  ssh-copy-id user@host
  ```

- **Add Key to SSH Agent**

  ```bash
  ssh-add /path/to/private_key
  ```

## File Transfer

- **Using SCP**
  - **Copy File to Server**

    ```bash
    scp file user@host:/path/on/server
    ```

  - **Copy Directory to Server**

    ```bash
    scp -r /local/dir user@host:/remote/dir
    ```

  - **Copy File from Server**

    ```bash
    scp user@host:/path/on/server/file /local/path
    ```

- **Using SFTP**

  ```bash
  sftp user@host
  ```

  - **SFTP Commands**:
    - `get remote_file` - Download a file
    - `put local_file` - Upload a file
    - `ls` - List files on the server
    - `exit` - Exit SFTP

## Port Forwarding

- **Local Port Forwarding**

  ```bash
  ssh -L local_port:destination_host:destination_port user@host
  ```

- **Remote Port Forwarding**

  ```bash
  ssh -R remote_port:destination_host:destination_port user@host
  ```

- **Dynamic Port Forwarding (SOCKS Proxy)**

  ```bash
  ssh -D local_port user@host
  ```

## Tunneling

- **SSH Tunneling with ProxyJump**

  ```bash
  ssh -J user@jumphost user@targethost
  ```

- **SSH Multiplexing**

  ```plaintext
  Host *
      ControlMaster auto
      ControlPath ~/.ssh/sockets/%r@%h-%p
      ControlPersist 600
  ```

## Miscellaneous

- **Run Command on Remote Server**

  ```bash
  ssh user@host "command"
  ```

- **Verbose Mode (for Debugging)**

  ```bash
  ssh -v user@host
  ```

- **Disable Host Key Checking (Use with Caution)**

  ```bash
  ssh -o StrictHostKeyChecking=no user@host
  ```

- **SSH Agent Forwarding**

  ```bash
  ssh -A user@host
  ```

## SSH Config File Tips

- **Sample Config Entry**

  ```plaintext
  Host myserver
      HostName example.com
      User username
      Port 22
      IdentityFile ~/.ssh/id_rsa
      ForwardAgent yes
  ```

## Common Issues

- **Fix "Permissions are too open" Error**

  ```bash
  chmod 600 ~/.ssh/id_rsa
  ```

- **Add Known Host**

  ```bash
  ssh-keyscan -H host >> ~/.ssh/known_hosts
  ```

---

This covers the essential SSH commands and configurations to streamline SSH usage!