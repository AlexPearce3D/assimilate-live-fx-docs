# 📰 Licensing the Software

## Activating the Software

When you first start the Assimilate Product Suite software or when an existing license expires, you are presented with the License dialog to activate your license key(s).&#x20;

![](http://www.assimilatesupport.com/akb/Uploads/Images/Manual/Live_Looks/01-Installation,%20Licensing%20and%20Startup/001_License_Dialog.png)

As of version 9.2, you can activate multiple license keys at once to combine products. Once activated, the license (s) are tied to the system and cannot be activated on another system. However, also as of version 9.2, you can deactivate a license. The procedure for this is described later in this article.

A license key is formatted as "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx" \
\
A total of 36 characters including the separators. You can enter the key manually or copy the key to the clipboard of Windows / OS X and use the **Paste** button. This will replace any key (s) that is already there. To add another key from the clipboard rather than replacing it, use the **Add** button. After entering one or more keys, the **Activate Key** button switches into an enabled state.

When you click the **Activate Key** button the software contacts the Assimilate activation server over the internet and sends the keys along with your system's details to validate the keys and generate a license for the system. If the key validates, the license is then automatically installed. A second dialog will pop up asking you to restart the software. On Windows this restart will be done automatically - on OS X the software will just close down and needs to be started manually again.

Note: The system needs a working internet connection for online activation.

### **License Activation and Privacy Policy**

When Activating the software with a license key, SCRATCH will send information about your system over the internet to Assimilate' server to create a license. The information sent is the same data as that which is written in a standard SCRATCH log file and contains information about the system hardware (CPU, Memory and GPU specifications), the Operating System (Type and version), and data items like system name, system-id and disk-id to identify the system to generate a system specific license for it.&#x20;

All information is sent over a secure (HTTPS) connection and is stored in the Assimilate database and only used for generating a license or referencing in case of a problem with SCRATCH and/or the license. This information will never be sold, traded, or otherwise distributed to another party.

## **Deactivating a License**

To un-tie a license from a system you need to deactivate the license key(s). However, you first need to explicitly **Unlock** a license key before it can be deactivated. This is an extra security step so that not anybody can just deactivate a license key and activate it on his/another system. To unlock a license key you need to login to the [MyAssimilate](https://myassimilate.assimilateinc.com/) website and you need to be registered as a license administrator.&#x20;

If you bought the license key on the online store then you are automatically a license administrator. If you are not registered as a license administrator, the MyAssimilate website will show a message and you should contact [licensing@assimilateinc.com](https://mail.google.com/mail/?view=cm\&fs=1\&tf=1\&to=licensing@assimilateinc.com).&#x20;

If you are a license administrator you will find all the license keys you own listed on the MyAssimilate site. Find the license key in question and click the corresponding gear icon at the end of the table row. This opens the **Update License** panel. There you click the **(Un)lock** button to _unlock_ or _re-lock_ a license key.

![](http://www.assimilatesupport.com/akb/Uploads/Images/Manual/Getting_Started/Licensing_software/license.png)

![](http://www.assimilatesupport.com/akb/Uploads/Images/Manual/Getting_Started/Licensing_software/wrench.png)

Note that if a license is un-locked a little un-locked icon is showing in the license key table.

## Licensing Issues and FAQ

For any licensing questions or issues, please read through this part of the manual. When the question or issue persists, contact [licensing@assimilateinc.com](https://mail.google.com/mail/?view=cm\&fs=1\&tf=1\&to=licensing@assimilateinc.com) and always include an Assimilator.log file with the request. If you experience problems with activating the software make sure to:

* The system has a working internet connection - you can check this by opening an internet browser on the computer and opening e.g. the Assimilate homepage at [http://www.assimilateinc.com](http://www.assimilateinc.com/).
* Check if any firewalls are blocking the system from connecting to the Assimilate server. A firewall can be switched on on the system itself or can be located elsewhere in the network. In the former situation, try switching off the firewall temporarily in the latter case - contact your network administrator.
* In some cases, you might get a 'key in use' message after activating. In that case, you either used a key that is already used by another system or either the system-id or disk-id of the system you are activating from has changed. Contact Assimilate and include both the latest log file and the key you are using to activate.

### **Updating a license**

To update an existing license file, open the licensing panel:

* In SCRATCH, use the **License** button in the Startup screen in the lower right section.
* In Play Pro, use the **License** button in the Construct screen in the lower right corner.
* In Live Looks / Live Assist (when used as a stand-alone tool), use the **License** button in the Setup pnale lower right corner.

### **Auto-renewal of Subscription Licenses**

If you have a monthly subscription with recurring payments, the license you obtain after activating will only be valid for a month. However, the software will automatically try to renew the license each month several days before it expires. The system needs to be online for the renewal to succeed. If the re-activation fails and the license expires, the license dialog will pop up.

### **Possible License Issues**

There are cases in which activation fails and an error message is displayed.&#x20;

* **Key in use**. The license key has been used to activate another system or the system configuration has changed (new hardware such as network adapter or hard disk) that the license has become invalid.
* **Invalid key**. You entered a key that is not recognized as a valid key - possibly by entering a wrong character. Check the license key carefully.
* **Activation failed - code X**. Where X is a number: 0 indicates that SCRATCH does not have a working internet connection - contact your system administrator or try to connect to the web using the standard browser on the system. Other codes are described here [http return codes](http://en.wikipedia.org/wiki/List_of_HTTP_status_codes).&#x20;
* **Subscription expired or is invalid**. Sell explanatory.
* **Error activating multiple trial keys**. You are not allowed to activate multiple trial licenses on a single system. Contact ASSIMILATE Sales for a solution.
* **E666**.You get this error when trying and failing to activate a key more than three times in a row. Wait 30 minutes and try again to see the real error.
* Other general errors are - _Failed to activate_, _Generator Error_, _E100_. Please make sure you entered the correct license key and contact ASSIMILATE Support if the issue persists.

### **Multiple License Keys**

You can activate multiple license keys on a single system to combine products - e.g. combine a Live Looks license key with a SCRATCH license key. The following rules apply when activating multiple keys together.

* The resulting license is valid for the shortest term of each of the individual licenses. If one of the license keys expires before the other, you need to re-activate the longer-term license explicitly again.
* You can only deactivate all licenses at ones and not separate. To move one of the license keys to another system - first, unlock all licenses (see above), then deactivate all the licenses at once, and then just activate the license that you want to remain on the system.
* If one of the licenses that you are trying to activate has an issue - the error message that is displayed will contain the (index) number of the license in the list, so you can easily isolate that.

### **Log Files**

The **Log Files** button will open the folder where SCRATCH maintains its application log files. The use and content of the log files are described later in this chapter.
