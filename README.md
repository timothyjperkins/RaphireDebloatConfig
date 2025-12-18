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
ACGMediaPlayer<br>
ActiproSoftwareLLC<br>
AdobeSystemsIncorporated.AdobePhotoshopExpress<br>
Amazon.com.Amazon<br>
AmazonVideo.PrimeVideo<br>
Asphalt8Airborne<br>
AutodeskSketchBook<br>
CaesarsSlotsFreeCasino<br>
Clipchamp.Clipchamp<br>
COOKINGFEVER<br>
CyberLinkMediaSuiteEssentials<br>
Disney<br>
DisneyMagicKingdoms<br>
DrawboardPDF<br>
Duolingo-LearnLanguagesforFree<br>
EclipseManager<br>
Facebook<br>
FarmVille2CountryEscape<br>
fitbit<br>
Flipboard<br>
HiddenCity<br>
HULULLC.HULUPLUS<br>
iHeartRadio<br>
Instagram<br>
king.com.BubbleWitch3Saga<br>
king.com.CandyCrushSaga<br>
king.com.CandyCrushSodaSaga<br>
LinkedInforWindows<br>
MarchofEmpires<br>
Microsoft.3DBuilder<br>
Microsoft.549981C3F5F10<br>
Microsoft.BingFinance<br>
Microsoft.BingFoodAndDrink<br>
Microsoft.BingHealthAndFitness<br>
Microsoft.BingNews<br>
Microsoft.BingSearch<br>
Microsoft.BingSports<br>
Microsoft.BingTranslator<br>
Microsoft.BingTravel<br>
Microsoft.BingWeather<br>
Microsoft.Copilot<br>
Microsoft.GamingApp<br>
Microsoft.Getstarted<br>
Microsoft.Messaging<br>
Microsoft.Microsoft3DViewer<br>
Microsoft.MicrosoftJournal<br>
Microsoft.MicrosoftOfficeHub<br>
Microsoft.MicrosoftPowerBIForWindows<br>
Microsoft.MicrosoftSolitaireCollection<br>
Microsoft.MixedReality.Portal<br>
Microsoft.NetworkSpeedTest<br>
Microsoft.News<br>
Microsoft.Office.Sway<br>
Microsoft.OneConnect<br>
Microsoft.People<br>
Microsoft.PowerAutomateDesktop<br>
Microsoft.Print3D<br>
Microsoft.ScreenSketch<br>
Microsoft.SkypeApp<br>
Microsoft.Windows.DevHome<br>
Microsoft.WindowsAlarms<br>
Microsoft.WindowsFeedbackHub<br>
Microsoft.WindowsMaps<br>
Microsoft.WindowsSoundRecorder<br>
Microsoft.Xbox.TCUI<br>
Microsoft.XboxApp<br>
Microsoft.XboxGameOverlay<br>
Microsoft.XboxGamingOverlay<br>
Microsoft.XboxIdentityProvider<br>
Microsoft.XboxSpeechToTextOverlay<br>
Microsoft.YourPhone<br>
Microsoft.ZuneMusic<br>
Microsoft.ZuneVideo<br>
MicrosoftCorporationII.MicrosoftFamily<br>
MicrosoftCorporationII.QuickAssist<br>
Netflix<br>
NYTCrossword<br>
OneCalendar<br>
PandoraMediaInc<br>
PhototasticCollage<br>
PicsArt-PhotoStudio<br>
Plex<br>
PolarrPhotoEditorAcademicEdition<br>
Royal Revolt<br>
Shazam<br>
Sidia.LiveWallpaper<br>
SlingTV<br>
Spotify<br>
TikTok<br>
TuneInRadio<br>
Twitter<br>
Viber<br>
WinZipUniversal<br>
Wunderlist<br>
XING<br>
