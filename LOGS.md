# Getting MetaMask Logs

If you've run into an issue, and reported it on [our Github](https://github.com/MetaMask/metamask-plugin/issues) or [our Slack](http://slack.metamask.io/), but we haven't been able to figure it out, we might ask you to get us some logs that you should submit [here](http://metamask.consensyssupport.happyfox.com/home) with your issue number or brief descrption of the problem that you are having. Do not post your logs publicly.

There are four types of logs that you might need to check:
- UI State Logs
- Popup Logs
- Background Logs
- Crash Logs

## UI State Logs (Chrome)

If you've had an issue sending transactions or found a visual glitch in the rendering of MetaMask, we might ask you for a UI State log.  To get one of these:

1. Open MetaMask and ensure its unlocked.
2. Click the menu in the top right, click "Settings".
3. Click the button that says "Copy State Logs".
4. It will copy something that looks like [this](https://github.com/MetaMask/metamask-plugin/blob/master/development/states/account-detail.json).
5. Upload it as a [gist](https://gist.github.com/) or to some other pastebin site 
6. Send the link to us, ideally in [a new Github issue](https://github.com/MetaMask/metamask-plugin/issues/new).


## Popup Logs (Chrome)

To get logs from the popup:

1. Click the MetaMask fox in the top right of your browser.
2. Wait for the popup to open (or partially open if that's part of the bug).
3. Right-click in the newly opened popup, and select `Inspect Element`.
4. Wait for the new `Inspector` window to open.
5. Click `Console` at the top of the `Inspector` window.
6. Look for any strange logs, especially red errors!

## Background Logs (Chrome)

To get logs from MetaMask's background process in Chrome:

1. Right-click the MetaMask fox in the top right of your browser.
2. Select `Manage Extensions`.

  ![image](https://cloud.githubusercontent.com/assets/1474978/22399076/f54b8d24-e549-11e6-9bf4-48bf8767f20d.png)

3. Ensure "Developer Mode" is selected in the top right.

  ![image](https://cloud.githubusercontent.com/assets/1474978/22398918/52c8e388-e546-11e6-92d5-dcf6daed7718.png)

4. Scroll down to `MetaMask`, and click the "Inspect views: `background page`" link.
5. Wait for the new `Inspector` window to open.
6. Click `Console` at the top of the `Inspector` window.
7. Look for any strange logs, especially red errors!

## Crash Logs (Chrome)

If your bug involves crashing the whole browser, then having a browser console won't be much good! (It will be crashed).

In these cases, you'll need to start your browser in a way that it writes its logs to the disk, so you can open that log file after the browser crashes.

[This process is described here](https://www.chromium.org/for-testers/enable-logging), and we hope to write more specific steps on this in the future. If you have to go through this process, please do record the steps, so we can have more detailed instructions here for different platforms.

In short this looks like:

1. Close all Google Chrome processes

2. Start chrome in the terminal
linux:
```
google-chrome --enable-logging=stderr
```
MacOS:
```
/Applications/Google\ Chrome.app/Contents/MacOS/Google\ Chrome --enable-logging=stderr
```

## Internal Storage (Chrome)

If your bug has been highly severe, and there is suspicion of a security issue, the most extreme kind of data you could provide is your MetaMask internal storage.

This includes your secret keys, used to control your accounts, encrypted with your password. You should never paste this data in public. MetaMask employees will never ask you for this data, unless you have already transferred all value away from that vault, and if you share this data, you give up all control over those accounts, so do it with the highest gravity.

If your account has no funds left in it, or if it was only a testnet account, it may be appropriate to send this information to a MetaMask developer.

Retrieve the data like this:

1. Follow the steps above to open the `Background Logs (Chrome)`.
2. Open the `Application` tab.
3. Click the arrow next to the `Local Storage` item on the left menu.
4. You should see an item called `chrome-extension://nkbi.....`.  Click this.
5. In the row whose Key is `metamask-config`, double click the `Value` column, to highlight the config, and copy it. It should start something like: `{"meta":{"version":11},"data":{...`.
6. Paste this into a text document, or somewhere safe, and send it to the trusted party to help debug.
