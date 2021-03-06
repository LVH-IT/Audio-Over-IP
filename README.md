# Realtime Audio over IP
This package uses the following external dependencies:
* [go-ole](https://github.com/go-ole/go-ole), which is licenced under an [MIT](https://github.com/go-ole/go-ole/blob/master/LICENSE) license.
* [go-wav](https://github.com/moutend/go-wav), which is licenced under an [MIT](https://github.com/moutend/go-wav/blob/master/LICENSE) license.
* [go-wca](https://github.com/moutend/go-wca), which is licenced under an [MIT](https://github.com/moutend/go-wca/blob/develop/LICENSE) license.
* [fyne](https://github.com/fyne-io/fyne), which is licenced under an [BSD 3-Clause "New" or "Revised"](https://github.com/fyne-io/fyne/blob/master/LICENSE) license.


## What does it do?
This program captures the system Audio of a Windows Computer and sends it to another Windows computer over the network in almost realtime.  
**BEWARE:** The audio stream is not encrypted. If you plan to use this Software to send an audio stream over an untrusted network, such as the internet for example, you should use something like an SSH tunnel to encrypt the stream.  


## Usage
Download the latest release and continue with "How to setup". There are no prerequisites when using the already compiled binary file.  
If you want to however, you can also compile the code yourself as explained below.  


### How to setup
You have to put the client executable on the computer on which you want to play an audio stream, and the server executable has to be on the computer from which you want to stream the system audio.  
You can then use the flags listed below to start the server and connect to it with a client.  

### Flags you can use
Client:
* **-cli** : to start the client in cli mode
    * **-e** : server address to connect to (ex: -e 127.0.0.1:4040), Has to be specified
    * **-v** : displays more info about the stream and the audio setup  

Server:  
* **-p** : port to listen on

### Limitations
* Both devices have to use the same audio device settings (ex: 16 Bit, 48000 Hz), as there is no audio resampler implemented yet  
* When the connection gets instable, the audio gets delayed by the amount of time the connection dropped  

## Compilation
### Prerequisites for compilation
Go 1.16 (https://golang.org/dl/)  
You'll get the rest when trying to compile  


### How to compile
You need to follow the next steps for each the server and the client:  
Open a command prompt in the source directory and you should be able to install all dependencies by executing this command inside the source folder: 
```sh
go get -d ./...
```
Then simply type:
```sh
go build
```
It will then try to compile and tell you whether there are dependencies that are still missing.
If so, you need to install them each like this for example: 
```sh
go get github.com/go-ole/go-ole
```
Then rerun "go build" and your executable should be compiled in the source directory.
