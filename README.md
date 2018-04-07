# colossus_server

This gets the data from the DAQ to all the devices that are trying to see it.  It is meant to be used with the [Colossus_website](https://github.com/cyficowley/colossus_website/).

# run

Run the python file `colossus_server/main.py` from the SEDS laptop. It establishes an ftp link with the DAQ and runs a flask api where the data can be requested from.  This requires a windows laptop because it has some weird dlls.

Then plug in the raspberry pi which will automatically start the websocket and start pushing the data to all connected devices on port 192.168.100:8080. (the actual ip address could possibly change but the port won't)

If it doesn't automatically start run `node ~/colossus_server/node/index.js` to start it up. All the startup configuration is done in `/etc/rc.local`.

The reason we have two different servers, the flask one just having one client and the node websocket one everyone else is because we are doing everything we can to save cpu on the seds laptop  and don't want to deal with running a legit server on windows.
