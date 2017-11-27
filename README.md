# [Gravitonium](https://gravitonium.org/) Desktop GUI Wallet

## Graphical user interface wrapper for the [Gravitonium](https://gravitonium.org/) command line tools

This program provides a Graphical User Interface (GUI) for the Gravitonium client tools that acts as a wrapper and presents the information in a user-friendly manner.

![Screenshot](docs/HUSHWallet.png "Main Window")

### Security warning
**Encryption of the `wallet.dat` file is not yet supported for Gravitonium. Using the wallet on a system infected**
**with malware may result in wallet data/funds being stolen. Such cases have been reported! In addition the**
**only way to have full assurance of the safety of running the node/wallet software is to compile it from**
**source code and to inspect the code first.**


## Building, installing and running the Wallet GUI

Before installing the Desktop GUI Wallet you need to have Gravitonium up and running. The following [guide](https://github.com/Graviteam/Gravitonium/blob/master/README.md) explains how to set up [Gravitonium](https://gravitonium.org/). 

**For security reasons it is recommended to always build the GUI wallet program from GitHub**
**[source](https://github.com/Graviteam/Gravitonium/archive/master.zip).**
The details of how to build it are described below (easy to follow). 

1. Operating system and tools

   As of May 2017 this program is mostly tested on Linux. The Linux tools you need 
   to build and run the Wallet GUI are Git, Java (JDK7 or later) and Ant. If using Ubuntu Linux, 
   they may be installed via command: 
   ```
   user@ubuntu:~/build-dir$ sudo apt-get install git default-jdk ant
   ``` 
   For RedHat/CentOS/Fedora-type Linux systems the command is (like):
   ```
   user@centos:~/build-dir$ sudo yum install java-1.8.0-openjdk git ant 
   ```
   The name of the JDK package (`java-1.8.0-openjdk`) may vary depending on the Linux system, so you need to
   check it, if name `java-1.8.0-openjdk` is not accepted.
   If you have some other Linux distribution, please check your relevant documentation on installing Git, 
   JDK and Ant. The commands `git`, `java`, `javac` and `ant` need to be startable from command line 
   before proceeding with build.

2. Building from source code

   As a start you need to clone the Gravitonium-GUI-Wallet Git repository:
   ```
   user@ubuntu:~/build-dir$ git clone https://github.com/Graviteam/Gravitonium-GUI-Wallet.git
   ```
   Change the current directory:
   ```
   user@ubuntu:~/build-dir$ cd Gravitonium-GUI-Wallet/
   ```
   Issue the build command:
   ```
   user@ubuntu:~/build-dir/Gravitonium-GUI-Wallet$ ant -buildfile ./src/build/build.xml
   ```
   This takes a few seconds and when it finishes, it builds a JAR file `./build/jars/GravitoniumSwingWalletUI.jar`. 
   You need to make this file executable:
   ```
   user@ubuntu:~/build-dir/Gravitonium-GUI-Wallet$ chmod u+x ./build/jars/GravitoniumSwingWalletUI.jar
   ```
   At this point the build process is finished the built GUI wallet program is the JAR 
   file `./build/jars/GravitoniumSwingWalletUI.jar`

3. Installing the built Gravitonium GUI Wallet

  3.1. If you have built Gravitonium from source code:

   Assuming you have already built it from source code in directory `/home/user/Gravitonium/src` (for 
   example - this is the typical build dir. for Gravitonium) which contains the command line tools `gravitonium-cli` 
   and `gravitoniumd` you need to take the created file `./build/jars/GravitoniumSwingWalletUI.jar` and copy it 
   to directory `/home/user/Gravitonium/src` (the same dir. that contains `gravitonium-cli` and `gravitoniumd`). Example copy command:
   ```
   user@ubuntu:~/build-dir/Gravitonium$ cp ./build/jars/GravitoniumSwingWalletUI.jar /home/user/Gravitonium/src    
   ```

4. Running the installed Gravitonium GUI Wallet

   Before running the GUI you need to start gravitoniumd (e.g. `gravitoniumd --daemon`). The wallet GUI is a Java program packaged 
   as an executable JAR file. It may be run from command line or started from another GUI tool (e.g. file manager). 
   Assuming you have already installed Gravitonium and the GUI Wallet `GravitoniumSwingWalletUI.jar` in 
   directory `/home/user/Gravitonium/src` one way to run it from command line is:
   ```
   user@ubuntu:~/build-dir/Gravitonium-GUI-Wallet$ java -jar /home/user/Gravitonium/src/GravitoniumSwingWalletUI.jar
   ```
   If you are using Ubuntu (or similar ;) Linux you may instead just use the file manager and 
   right-click on the `GravitoniumSwingWalletUI.jar` file and choose the option "Open with OpenJDK 8 Runtime". 
   This will start the Gravitonium GUI Wallet.
   
   **Important:** the Gravitonium configuration file `~/.gravitonium/gravitonium.conf` needs to be correctly set up for the GUI
    wallet to work. Specifically the RPC user and password need to be set in it like:
    ```
    rpcuser=username
    rpcpassword=wjQOHVDQFLwztWp1Ehs098LKJHAXjd4E
    
    ``` 

### License
This program is distributed under an [MIT License](https://github.com/Graviteam/Gravitonium-GUI-Wallet/raw/master/LICENSE).

### Disclaimer

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
