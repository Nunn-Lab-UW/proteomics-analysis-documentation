Connecting to a GSIT (Nexus) via SSH
=====================================

This guide provides instructions for connecting to a remote server using SSH on both macOS and Windows.

macOS
-----

Connecting to a remote server from macOS is straightforward using the built-in Terminal application.

1.  **Open the Terminal application:**
    You can find the Terminal application in ``Applications -> Utilities -> Terminal``. A quicker way to open it is to use Spotlight Search by pressing ``Cmd + Space``, typing ``Terminal``, and pressing ``Enter``.

2.  **Connect using SSH:**
    Once the terminal is open, you can connect to the remote server using the ``ssh`` command, followed by your username and the server's address.

    .. code-block:: bash

       ssh your_username@nexus.gs.washington.edu

    For example, if your username is ``mriffle``, you would use:

    .. code-block:: bash

       ssh mriffle@nexus.gs.washington.edu

    The first time you connect, you may see a message asking you to verify the authenticity of the host. Type ``yes`` and press ``Enter`` to continue. You will then be prompted to enter your password.

Windows
-------

Connecting to a remote server from Windows has become much easier with modern versions of Windows, which include a built-in SSH client. For the best experience, we recommend using the Windows Terminal.

Installing Windows Terminal
~~~~~~~~~~~~~~~~~~~~~~~~~~~

Windows Terminal is a modern, powerful terminal application for users of command-line tools and shells like Command Prompt, PowerShell, and WSL. If you are on Windows 11, Windows Terminal is likely already installed.

Its main features include multiple tabs, panes, Unicode and UTF-8 character support, a GPU accelerated text rendering engine, and custom themes, styles, and configurations.

If it is not already installed, you can get it from the Microsoft Store:

1.  **Open the Microsoft Store** on your Windows computer.
2.  Search for **"Windows Terminal"**.
3.  Click the **"Get"** or **"Install"** button to download and install it.

Alternatively, you can install it using the `winget` command-line tool:

.. code-block:: bash

   winget install -e --id Microsoft.WindowsTerminal

Connecting with SSH
~~~~~~~~~~~~~~~~~~~

Once you have Windows Terminal installed, you can use it to connect to your remote server.

1.  **Open Windows Terminal.**
    You can find it in your Start Menu. You can also right-click the Start button and select "Terminal".

2.  **Connect using SSH:**
    The command to connect is the same as on macOS and Linux. You will use the `ssh` command, followed by your username and the server's address.

    .. code-block:: bash

       ssh your_username@nexus.gs.washington.edu

    For example, if your username is `mriffle`, you would use:

    .. code-block:: bash

       ssh mriffle@nexus.gs.washington.edu

    The first time you connect, you will be asked to confirm the authenticity of the host. Type `yes` and press `Enter`. You will then be prompted for your password.

Preventing SSH Timeouts
-----------------------

.. note::

   This is an optional step. By default, your SSH connection may time out after a period of inactivity. If you find this happening frequently, you can configure your SSH client to send a "keepalive" signal to the server to keep the connection active.

macOS
~~~~~

On macOS, you can configure this in the ``~/.ssh/config`` file.

1.  **Open a terminal** and use a text editor to create or open the SSH config file. For example, using `nano`:

    .. code-block:: bash

       nano ~/.ssh/config

2.  **Add the following lines** to the file:

    .. code-block:: text

       Host *
           ServerAliveInterval 120

    This configuration applies to all hosts (``*``) and sends a keepalive signal every 120 seconds.

3.  **Save and exit** the editor. For `nano`, press ``Ctrl + X``, then ``Y`` to confirm, and ``Enter``.

Windows
~~~~~~~

The process is similar on Windows. The SSH config file is located at ``C:\Users\<Your-Username>\.ssh\config``.

1.  **Open File Explorer** and navigate to your user profile directory (e.g., ``C:\Users\mriffle``).

2.  If you don't see a ``.ssh`` folder, you may need to show hidden files. In File Explorer, go to the **View** tab and check the **Hidden items** box.

3.  Open the ``.ssh`` folder. If a file named ``config`` does not exist, create it.

4.  **Open the ``config`` file** with a text editor like Notepad.

5.  **Add the following lines**:

    .. code-block:: text

       Host *
           ServerAliveInterval 120

6.  **Save the file** and close the editor. Your SSH connections will now use these settings.
