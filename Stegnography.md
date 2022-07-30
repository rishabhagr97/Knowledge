# Steganography
## steghide
```bash
steghide extract -sf <imagename>
```
-	Used to hide data in jpeg file
-	Also have feature to hide data with password encryption.
## zsteg
```bash
zsteg <imagename>
```
-	Used to extract hidden text from png file
-	Uses various payloads to decrypt encrypt data
## Exiftool
```bash
Exiftool <filename>
```
-	Useful to extract hidden text from file metadata.
## Stegoverites
```bash
stegoverites <filename>
```
-	Applies all previous techniques + advance extraction to a file
-	Also shows image in different contrasts
## sonic-visualizer
```bash
A GUI tool
```
-	Visually show text hidden in audio wavelength.
-	Open sonic visualizer. From there click Layer->Add Spectrogram and you should see hidden text. Press + to zoom it.
