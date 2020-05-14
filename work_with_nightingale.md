#Set up account
1. Email to request an account and cc Judy

#Log-in
1. In terminal, type ```ssh NETID@nightingale.ucsd.edu``` and enter password

#Initialize (install Jupyter  / Conda)
1. Install Anaconda3 by ```wget https://repo.continuum.io/archive/Anaconda3-2020.02-Linux-x86_64.sh``` (the date should be changed to the latest version)
2. ```ls``` and find the file name (which is Anaconda3-2020.02-Linux-x86_64.sh in this case)
3. ```bash Anaconda3-2020.02-Linux-x86_64.sh``` so Anaconda3 would be installed
3. Close and reopen terminal

#Connect nightingale
1. *Connect to campus VPN*
2. ```ssh NETID@nightingale.ucsd.edu``` and log in with ucsd password
3. ```conda activate```
4.```jupyter notebook --port 8889``` (it can be any 4-digit)
5. Open a new command window that's on local but not on nightingale ```ssh -fNL 8889:localhost:8889 NETID@nightingale.ucsd.edu```
6. Go to "localhost:8889" in your browser and it shall work!
