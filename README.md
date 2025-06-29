PowerShell to validate HKLM\SOFTWARE\Microsoft\Shared Tools\Web Server Extensions\16.0\Secure\FarmAdmin\CredentialKeyDPEnt SharePoint Server stores Masterkey in an encrypted form in registry by using the Farm Guid as the salt/entropy and Dpapi with local machine keys as the encryption/decryption service used. Sometimes, when there are issues like Farm PassPhrase lost, not in sync on server etc, it becomes important to check the status of this key.

This script uses SharePoint methods in SPCredentialManager and SPFARM to fetch the key. Essentially what it will do is that it will get the current reg value and then use the Farm ID guid as the salt/entropy and call the Dpapi to decrypt the reg value using machine keys. If it returns the decrypted value, that confims that the HKLM\SOFTWARE\Microsoft\Shared Tools\Web Server Extensions\16.0\Secure\FarmAdmin\CredentialKeyDPEnt is fine and working. Decrypted value is referred to as Masterkey in SharePoint internally.

Can be a savior in specific SharePoint passphrase forgotten/not working scenarios.

Created by Anshuman Gupta anshug@microsoft.com/zanshgptz@gmail.com
