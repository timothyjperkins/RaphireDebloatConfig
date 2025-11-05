Script to download a custom set of Win10/11 apps to uninstall and then run Raphire Debloat against that list.
https://github.com/Raphire/Win11Debloat
All credit goes to Raphire for this incredible script!
By default, his script would remove Microsoft Sticky Notes. Yes, it's deprecated now in favor of OneNote, but many of my users still use it, and if it's removed, all of their data in the sticky notes goes with it.
This config specifically does not remove Microsoft Sticky Notes. There are a few additional programs (see below) that my configuration removes.

PowerShell script to download the file and run the amazing debloat provided by Raphire:

----- Begin Script -----
# Define target folder and file URL
$targetFolder = Join-Path $env:TEMP "Win11Debloat"
$fileName = "CustomAppsList"
$targetFile = Join-Path $targetFolder $fileName

# Use the RAW GitHub file URL
$fileUrl = "https://raw.githubusercontent.com/timothyjperkins/RaphireDebloatConfig/main/CustomAppsList"

# Create folder if it doesn't exist
if (-not (Test-Path $targetFolder)) {
    New-Item -ItemType Directory -Path $targetFolder -Force | Out-Null
}

# Download the file
Invoke-WebRequest -Uri $fileUrl -OutFile $targetFile -UseBasicParsing

# Confirm success
Write-Host "File downloaded successfully to $targetFile"

# Set the Execution Policy so scripts will run
Set-ExecutionPolicy Unrestricted -Scope Process -Force

# Run Raphire Win11 Debloat with the custom app removal list (silently)
& ([scriptblock]::Create((irm "https://debloat.raphi.re/"))) -RemoveAppsCustom -Silent

----- End Script -----

You may want PowerShell to run a "Set-ExecutionPolicy Restricted -Scope Process -Force" afterwards if you want to ensure the computer is locked down again.

----- List of Apps to be Removed (note the lack of Microsoft.MicrosoftStickyNotes) -----
ACGMediaPlayer
ActiproSoftwareLLC
AdobeSystemsIncorporated.AdobePhotoshopExpress
Amazon.com.Amazon
AmazonVideo.PrimeVideo
Asphalt8Airborne
AutodeskSketchBook
CaesarsSlotsFreeCasino
Clipchamp.Clipchamp
COOKINGFEVER
CyberLinkMediaSuiteEssentials
Disney
DisneyMagicKingdoms
DrawboardPDF
Duolingo-LearnLanguagesforFree
EclipseManager
Facebook
FarmVille2CountryEscape
fitbit
Flipboard
HiddenCity
HULULLC.HULUPLUS
iHeartRadio
Instagram
king.com.BubbleWitch3Saga
king.com.CandyCrushSaga
king.com.CandyCrushSodaSaga
LinkedInforWindows
MarchofEmpires
Microsoft.3DBuilder
Microsoft.549981C3F5F10
Microsoft.BingFinance
Microsoft.BingFoodAndDrink
Microsoft.BingHealthAndFitness
Microsoft.BingNews
Microsoft.BingSearch
Microsoft.BingSports
Microsoft.BingTranslator
Microsoft.BingTravel
Microsoft.BingWeather
Microsoft.Copilot
Microsoft.GamingApp
Microsoft.Getstarted
Microsoft.Messaging
Microsoft.Microsoft3DViewer
Microsoft.MicrosoftJournal
Microsoft.MicrosoftOfficeHub
Microsoft.MicrosoftPowerBIForWindows
Microsoft.MicrosoftSolitaireCollection
Microsoft.MixedReality.Portal
Microsoft.NetworkSpeedTest
Microsoft.News
Microsoft.Office.OneNote
Microsoft.Office.Sway
Microsoft.OneConnect
Microsoft.People
Microsoft.PowerAutomateDesktop
Microsoft.Print3D
Microsoft.ScreenSketch
Microsoft.SkypeApp
Microsoft.Todos
Microsoft.Windows.DevHome
Microsoft.WindowsAlarms
Microsoft.WindowsFeedbackHub
Microsoft.WindowsMaps
Microsoft.WindowsSoundRecorder
Microsoft.Xbox.TCUI
Microsoft.XboxApp
Microsoft.XboxGameOverlay
Microsoft.XboxGamingOverlay
Microsoft.XboxIdentityProvider
Microsoft.XboxSpeechToTextOverlay
Microsoft.YourPhone
Microsoft.ZuneMusic
Microsoft.ZuneVideo
MicrosoftCorporationII.MicrosoftFamily
MicrosoftCorporationII.QuickAssist
MSTeams
Netflix
NYTCrossword
OneCalendar
PandoraMediaInc
PhototasticCollage
PicsArt-PhotoStudio
Plex
PolarrPhotoEditorAcademicEdition
Royal Revolt
Shazam
Sidia.LiveWallpaper
SlingTV
Spotify
TikTok
TuneInRadio
Twitter
Viber
WinZipUniversal
Wunderlist
XING
