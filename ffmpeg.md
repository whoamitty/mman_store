-------------------------------------------------------------------------------------
Conversion de fichier audio ou vidéo
-------------------------------------------------------------------------------------
> ffmpeg -i musique.wav musique.mp3
> ffmpeg -i video.avi video.mp4

-------------------------------------------------------------------------------------
Changer de format (sans ré-encodage)
-------------------------------------------------------------------------------------
> ffmpeg -i video.mp4 -c copy video.avi

-------------------------------------------------------------------------------------
Extraire la partie audio d'une vidéo
-------------------------------------------------------------------------------------
> ffmpeg -i video.mp4 audio.mp3

-------------------------------------------------------------------------------------
Couper le son d'une vidéo
-------------------------------------------------------------------------------------
> ffmpeg -i video.mp4 -vcodec copy -an out.mp4

-------------------------------------------------------------------------------------
Extraire une partie de fichier audio ou vidéo
-------------------------------------------------------------------------------------
> ffmpeg -i video.mp4 -ss 00:00:10 -c copy -to 00:00:15 out.mp4

-------------------------------------------------------------------------------------
Scinder un fichier en 2 parties
-------------------------------------------------------------------------------------
> ffmpeg -i video.mp4 -t 00:00:10 -c copy part1.mp4 -ss 00:00:10 -c copy part2.mp4

-------------------------------------------------------------------------------------
Fusionner plusieurs fichiers en un seul
-------------------------------------------------------------------------------------
> ffmpeg -f concat -i info.txt -c copy out.mp4

ffmpeg -i lauberge_espagnol.mp4 -ss 01:25:28 -to 01:25:40 -c copy test_lauberge_espagnol.mp4 
ffmpeg -i a.ogg -ss 00:01:02 -to 00:01:03 -c copy x2.ogg
ffmpeg -i a.ogg -ss 00:01:02.500 -t 00:01:03.250 -c copy x2.ogg






La durée peut être présente sous deux formats. ( FFmpeg 4.3 ou plus récent)

Format 1 :

[-][HH:]MM:SS[.m...]
ou

Format 2 :

[-]S+[.m...][s|ms|us]
Format 1 échantillons

01:20:10        1 hour 20 minute 10 seconds
04:03           4 minutes 3 seconds
07:02:05.100    7 hours 2 minutes 5 seconds 100 miliseconds 
Formater 2 échantillons

120             120 seconds
120.2           120.2 seconds or 120 seconds 200 miliseconds
1200ms          1200 milliseconds
1300us          1300 microseconds
Je ne compte jamais sur les décimales. Si possible, utilisez toujours format2 (-ss '120534ms').

ffmpeg -i a.ogg -ss '100ms' -t '600ms' -c copy x2.ogg
