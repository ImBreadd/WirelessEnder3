# WirelessEnder3
Wireless setup for the Ender3 using a Raspberry Pi with OctoPrint


## Objective

This project aims to enhance the functionality of an **Ender 3 3D printer** by enabling wireless control and remote monitoring using a **Raspberry Pi** running **OctoPrint**. The Ender 3, by default, doesn't have built-in Wi-Fi printing capabilities. By integrating OctoPrint, this project adds the ability to manage prints, monitor progress, and control the printer remotely, improving overall efficiency and usability.

## Features

- **Remote Control**: Start, stop, and pause prints from any device with a web browser.
- **Live Monitoring**: View a live feed of your 3D print via webcam integration.
- **Print Management**: Upload and manage print files directly from a web interface.
- **Print Progress**: Monitor print status in real-time (e.g., temperature, progress bar).
- **Automated Workflow**: Schedule, cancel, and control multiple prints wirelessly.

## Components Needed
- [x] Raspberry Pi (Model 3)
- [x] Ender 3 3D Printer
- [x] MicroSD Card
- [x] Camera

## Software

- **OctoPrint**: Open-source 3D printer management software running on the Raspberry Pi.
- **OctoPi**: A Raspbian-based OS for the Raspberry Pi pre-configured to run OctoPrint.
- **Web Interface**: Accessible via any device's browser for remote management.

## Setup Instructions

### Installing OctoPrint

1. Download [Raspberry Pi Imager](https://www.raspberrypi.com/software/)
2. Insert SD card into your pc
	*If you don't have an SD card slot you can get a [USB adapter](https://www.amazon.co.uk/Reader-High-Speed-Micro-Memory-Adapter-Supports-BLACK/dp/B0DBQKF2B4?source=ps-sl-shoppingads-lpcontext&ref_=fplfs&psc=1&smid=A1ZJ9F647UT3DX)*
	*If you have bought the Ender 3 it should've come with a SD card adapter, you can use that*

![Raspberry Pi Imager](https://github.com/user-attachments/assets/b1a7e1db-d716-4039-be88-d15cc351ab75)

4. Choose OS
5. Scroll down until you find Other specific-purpose OS

![Other specific-purpose OS](https://github.com/user-attachments/assets/ffc08b46-0ca0-4c2a-a8af-9bd5d726cd37)

6. Select 3D printing

![3D Printing](https://github.com/user-attachments/assets/140387e9-96ff-45e0-b374-1e676ff89bab)

7. Select OctoPi

![OctoPi](https://github.com/user-attachments/assets/3b3d6270-4977-42ae-aaeb-288a1c29c2b5)

8. Choose either stable or new camera stack
	*I chose new camera stack because I wanted to explore various monitoring methods*
9. Choose your device
	*I used the Raspberry Pi 3 Model B*
10. Choose the SD card you inserted earlier and hit next
11. Open advance options and set your SSID (the name of your wifi) and your wifi password
12. Set up the username and password to be something memorable and secure, you will need this later
13. If you set your hostname make sure you remember it, if you do not set your hostname your printer will be accessible with http://octopi.local. I set my hostname to "printer" so I access my printer through http://printer.local. 
14. You can now install the OS.
> [!NOTE] Do not format the SD card even if you are prompted to do so, this will break the install.

### Printer Setup


> [!NOTE] Make sure there is an SD card in your 3D printer, you will need this so you can upload gcode files to your printer.


![Setup photo](https://github.com/user-attachments/assets/031299db-4132-420d-b779-4fbe2650cbf4)

I used a USB cable to connect my Raspberry Pi to my printer.

> [!NOTE] Make sure your 3D printer is switched on. I made the mistake of thinking it was on because it connected on OctoPrint. Your RaspberryPi is capable of powering your printer, but it cannot power it while it is printing!

Go to your web interface for OctoPi. This will be http://octopi.local by default, or http://yoursethostname.local if you set a hostname during installation. You should come to a page that looks like this:

![OctoPrint pre-connect](https://github.com/user-attachments/assets/2bb2cfb5-54b0-41a9-8cb7-ef4442116643)

Once you've plugged your printer in you should be able to hit connect and your printer will automatically connect to OctoPrint. Once you've done that your interface should look like this: 

![OctoPrint after connect](https://github.com/user-attachments/assets/5d41e852-df66-40f2-925f-14ba0fb0bac4)

From here you can upload print files to the SD card in your printer and run prints. You can also set as well as monitor extruder temperature and bed temperature. Once you have sent a print it will calculate the amount of time your printer will take to complete the print.

At this point you have a way to send files to your printer and print them from your computer. 

### UltiMaker Cura

During my 3D printing journey, I discovered that my printer was unable to directly read and process STL files. In search of a solution, I explored various options online and came across [Cura](https://ultimaker.com/software/ultimaker-cura/), a free and widely used slicing software. Cura enables the conversion of STL files into G-code, making them compatible with my printer. Additionally, the software offers built-in functionality for monitoring print progress. However, since my printer lacks networking capabilities, utilizing this feature required additional setup and modifications.

1. Go to Marketplace in the top right corner
2. Search "Octoprint" and it should come up with [OctoPrint Connections](https://marketplace.ultimaker.com/app/cura/plugins/fieldofview/OctoPrintPlugin)
3. Install the Plugin and reset Cura
4. Add your printer to Cura as a non-networked printer
5. Go to Settings > Printer > Manager Printers
6. Select your printer and you should see a Connect OctoPrint button

![Ender 3 Connect](https://github.com/user-attachments/assets/661c3afe-f3d2-430c-9a91-b26fa68c7e93)

7. Click Connect OctoPrint
8. Your printer should show up in the list
	1. If it doesn't click Add
	2. Set your instance name as whatever you want it to be
	3. Set your IP Address or Hostname to the link you use to access OctoPrint (http://octopi.local by default)
	4. Click Ok
	5. This should prompt you to enter your username and password for OctoPrint
	6. Once you have entered the username and password authorise Cura and this should've generated an API key for Cura
> [!NOTE] DO NOT SHARE THIS WITH ANYONE
9. Click connect and now you can use Cura to slice 3D files and send them directly to your printer to print

If done correctly you should see this in the bottom right corner once you slice your model.

![Print with OctoPrint](https://github.com/user-attachments/assets/f8dc4e50-4ebb-4905-a703-f46396356889)


Just hit Print with OctoPrint and your printer should start printing.

![OctoPrint Start](https://github.com/user-attachments/assets/1a07ee09-b5e2-4b6e-a398-a1a3482daabc)

![IMG_2013(1)](https://github.com/user-attachments/assets/a151d068-c804-4ee4-93cf-bc022e5347de)

Now you have a simple way to both slice and print in one location.

