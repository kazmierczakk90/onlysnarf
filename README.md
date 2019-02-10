# OnlySnarf
  
`git clone git@github.com:skeetzo/onlysnarf`

## Scripts
First run:  
  * `(sudo) python3 setup.py install`  
Then from within project directory either:  
  * `(sudo) onlysnarf [args]`
  * `(sudo) onlysnarf-menu [args]`
  * `(sudo) onlysnarf-config [args]`
  * OR directly via `python3 onlysnarf.py (-d) -i|-g|-v`

## args

-d (ebug)  
  `python3 onlysnarf.py -d`  
Tests configuration. Does not upload or remove from Google Drive.

-i (mage)  
  `python3 onlysnarf.py -i`  
Uploads an image labeled: 'imageName - %d%m%y'  

-g (allery)  
  `python3 onlysnarf.py -g`  
Uploads a gallery labeled: 'folderName - %d%m%y'  

-v (ideo)  
  `python3 onlysnarf.py -v`  
Uploads a video labeled: 'folderName - %d%m%y'  

-t (ext)  
  `python3 onlysnarf.py -v -t "your mom"`  
Uploads a video labeled: 'your mom - %d%m%y'  

-h (ashtag)  
  `python3 onlysnarf.py -h`  
Uploads a video with the source folder split into hash tags: '#folderName'  

-f (orce upload)  
  `python3 onlysnarf.py -f`  
Attempts to upload limit regardless of file size. 

## Description

Downloads a random file or gallery of files from a random Google Drive folder as specified by run time arguments and then uploads the image, video, or gallery to an OnlyFans account.

`onlysnarf-menu` is used to easily perform basic sets of operations that would usually be time consuming for a long video upload ie waiting an hour until completion and then clicking send.

## Authentication
from [Auth Quickstart)(https://raw.githubusercontent.com/gsuitedevs/PyDrive/master/docs/quickstart.rst)
--------------
Drive API requires OAuth2.0 for authentication. *PyDrive* makes handles complex authentication steps that need to be personally authorized for your Drive account.

1. Go to `APIs Console`_ and make your own project.
2. Search for 'Google Drive API', select the entry, and click 'Enable'.
3. Select 'Credentials' from the left menu, click 'Create Credentials', select 'OAuth client ID'.
4. Now, the product name and consent screen need to be set -> click 'Configure consent screen' and follow the instructions. Once finished:

 a. Select 'Application type' to be *Web application*.
 b. Enter an appropriate name.
 c. Input *http://localhost:8080* for 'Authorized JavaScript origins'.
 d. Input *http://localhost:8080/* for 'Authorized redirect URIs'.
 e. Click 'Create'.

5. Click 'Download JSON' on the right side of Client ID to download **client_secret_<really long ID>.json**.

The downloaded file has all authentication information of your application.
**Rename the file to "client_secrets.json" and place it in the OnlySnarf folder.**

## Config
##### config.json  
Create or update the "config.json" file with the following values:
  * username -> OnlySnarf username  
  * password -> OnlySnarf password  
  * images_folder -> Google Drive folder id  
  * galleries_folder -> Google Drive folder id  
  * posted_folder -> Google Drive folder id  
  * videos_folder -> Google Drive folder id  

##### google_creds.txt   
Generated by Google Drive's authentication process. Saves Google authentication for repeat access.

##### settings.yaml  
Used to facilitate Google Drive's python authentication. Requires generating an app w/ credentials via Google Console. Credentials are authenticated once and then saved to "google_creds.txt". Does not need to be changed.

## Example Crons  

Upload an image once a day at noon:  
  `* 12 * * * python3 onlysnarf.py -i`

Upload a gallery of images every Wednesday at 2:30pm:  
  `30 14 * * 3 python3 onlysnarf.py -g`

Upload a random video every Friday in the month of June at 6:00pm:  
  `00 18 * 6 5 python3 onlysnarf.py -v`

## Dependencies
  * Chromedriver: binary installed via package

