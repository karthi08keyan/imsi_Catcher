# imsi_Catcher

# Hardware and Installation of tools
RTL-SDR
      Hackrf
      USRP
      Blade-RF
     
# Software
GR-GSM - A python module, which is used for receiving information transmitted by GSM.
Wireshark - Capturing the wireless traffic.
IMSI-Catcher - This program shows the IMSI number, country, brand and operator of cellphones.
GQRX – Software defined radio receiver.
RTL-SDR Tools – Get the information of the RTL SDR dongle.
Kailbrate – Determine the signal strength
# Installation of Wireshark, GQRX, GR-GSM, rtl-sdr
sudo apt-get update

 sudo apt-get install gnuradio gnuradio-dev git cmake autoconf libtool pkg-config g++ gcc make libc6 libc6-dev libcppunit-1.14-0 libcppunit-dev swig doxygen liblog4cpp5v5 liblog4cpp5-dev python3-scipy gr-osmosdr libosmocore libosmocore-dev rtl-sdr osmo-sdr libosmosdr-dev libboost-all-dev libgmp-dev liborc-dev libboost-regex-dev python3-docutils build-essential automake librtlsdr-dev libfftw3-dev gqrx wireshark tshark

 git clone -b maint-3.8 https://github.com/velichkov/gr-gsm.git

cd gr-gsm

mkdir build

cd build

cmake ..

make

sudo make install

sudo ldconfig

export PYTHONPATH=/usr/local/lib/python3/dist-packages/:$PYTHONPATH
# Installation of Kalibrate
 sudo apt-get update

git clone https://github.com/steve-m/kalibrate-rtl

cd kalibrate-rtl

./bootstrap && CXXFLAGS='-W -Wall -O3'

./configure

make

sudo make install
# Installation of IMSI Catcher
sudo apt install python-numpy python-scipy python-scapy

git clone https://github.com/Oros42/IMSI-catcher.git
# What is SDR?
Software Defined Radio is a radio broadcast communication technology, which is based on a software-defined wireless communication protocol instead of being implemented through hard-wires. SDR allows easy signal processing and experimentation with more complex radio frequency
# What is RTL-SDR?
RTL-SDR is a Realtek (RTL2832U) TV stick. TV sticks allow transmission of raw I/O samples, which can be used for DAB / DAB + / FM demodulation.
# What is GSM? 
GSM stands for Global System for Mobile communication. More than 5 billion people use GSM technology to communicate all over the world. Operators in every country use a different frequency in the GSM possible spectrum. Refer to https://www.worldtimezone.com/gsm.html 
# What is IMSI?
IMSI stands for “International Mobile Subscriber Identity” and is globally unique for each subscriber. The IMSI consists of 15 digits, which contain the Mobile Country Code (MCC), Mobile Network Code (MNC) and the Mobile Subscriber Identification Number (MSIN). The IMSI is stored in the Subscriber Identity Module (SIM)
# 2.Architecture of GSM!
Mobile Station (MS)

The mobile station is a device that can access the GSM network via radio. The mobile station can be broken down into two separate parts, the mobile hardware and the SIM card.

Base Station (BS)

Base Station is the antenna and is also called the “cell tower” or “cell site”. One BS covers a cellular area in the cellular network. The size of this cell can vary from a few hundred meters to several kilometers. The size of the cell area depends on the landscape features and the population density of the area. In subway stations and large buildings, relay stations can be placed to act as repeaters. These relay stations then wire the signal to the nearest base station.

Base Station Controller (BSC)

The base station controller controls several base stations. It handles the session handoffs between the different base stations when a user is moving through different cells. If the base stations are not connected to the same BSC, then the Mobile Switching Center (MSC) handles the handover.

Mobile Switching Center (MSC)

The mobile switching center is responsible for managing the authentication, handover to the other BSCs and routing calls to the landline.

Visitor Location Register (VLR)

Each MSC has its own Visitor Location Register (VLR). The VLR holds subscriber information of subscribers that are under the care of the MSC (which are copied from the Home Location Register (HLR)). The VLR, for example, holds the Temporary Mobile Subscriber Identity (TMSI), which is a temporary alias for the IMSI. This is to reduce the frequent broadcasting of the IMSI.

Home Location Register (HLR)

The HLR stores personal subscriber information like the IMSI and the phone number. There is only one HLR for every GSM network provider.

Authentication Center (AUC)

The Authentication Center (AUC) handles the authentication process of a subscriber to the network. More specifically, the AUC holds the shared secret key and generates the random challenge that is used to authenticate.
# How IMSI Catcher works?
IMSI Catchers are devices that act like fake cell towers, which trick a target’s device to connect to them and then relay the communication to an actual cell tower of the network carrier. The target’s communications in the form of calls, text messages, internet traffic etc. go through the IMSI Catcher, which can read messages, listen to the calls and so on. At the same time victim will have no knowledge that this is happening as everything will seemingly work as normal. This is referred to as Man-In-Middle attacks in security fields.

This is possible because of a loophole in GSM protocol. Mobile phones are always looking for the mobile tower with the strongest signal to provide the best commutation. This is usually the nearest one. At the same time, when a device connects to a cell tower, it authenticates to it via an IMSI number. However, the tower doesn’t have to authenticate back. This is why every time someone places a device that acts as a cell tower near your phone, it would connect to it and give away its IMSI.


