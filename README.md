@echo off
REM Change directory to where the file is
cd "C:\Pfad\zum\Verzeichnis"

REM Find the CSV file matching the pattern
for %%f in (file_*.csv) do set FILE_TO_ENCRYPT=%%f

REM Set output file name
set ENCRYPTED_FILE=%FILE_TO_ENCRYPT%.gpg

REM Set recipient
set RECIPIENT_EMAIL=recipient@example.com

REM Encrypt the file
gpg --encrypt --recipient %RECIPIENT_EMAIL% --output %ENCRYPTED_FILE% %FILE_TO_ENCRYPT%

echo File %FILE_TO_ENCRYPT% encrypted successfully as %ENCRYPTED_FILE%!
pause
