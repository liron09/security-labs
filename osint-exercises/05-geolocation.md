# Case Study: Image Geolocation & Metadata Extraction

**Type:** GEOINT / IMINT · **Program:** OSINT Analyst Program (Reichman University & Google)

## Part A: Geolocating a photo set

| # | Location found | How |
|---|---|---|
| 1 | **Panská street, Old Town, Bratislava (Slovakia)**, Pressburg Bajgel bakery | Reverse image search for the area; AI-assisted transcription of shop signs to pin the exact storefront |
| 2 | **Hodžovo námestie, Bratislava** | Broke the scene into anchors: a Hungarian flag on the right-hand building (embassy), a Czech-style fire vehicle, a building with black and purple lettering. Cross-referenced to the square, which has the Presidential Palace, the Hungarian embassy and the Astoria Palace office building. |
| 3 | **Kilometer Zero marker, Bratislava** | Reverse image search, validated across Yandex, Sogou and Shutterstock |
| 4 | **Gorkého ulica, Bratislava** | Spotted a dentist advertisement above a McDonald's sign, found the same ad in an Instagram post tagged "斯洛伐克" (Slovakia), then confirmed the street |
| 5 | **Road L4001 near Heiligenkreuz, Wienerwald (Lower Austria)**, next to the VinziRast am Land farm project | **EXIF extraction:** GPS coordinates; device Samsung Galaxy S24 Ultra (released January 2024, so the photo is recent, consistent with green vegetation); altitude 230 m, within mobile-GPS error of the area and consistent with low hills rather than the Alps. Verified with pic2map and Picarta. |

## Part B: Learning from the community
Studied OSINT geolocation communities and write-ups (r/WhereIsThis, @Quiztime on X, Medium OSINT newsletters) and broke down one write-up's methodology:

1. **Anchor identification:** football pitch, slope between photographer and pitch, Mediterranean architecture and vegetation, a distinctive building.
2. **Regional narrowing:** architecture and vegetation narrow it to the Mediterranean basin.
3. **Reverse image search** for the specific pitch.
4. **Satellite verification:** confirm the slope and building footprint.
5. **Street View match** against the original photo.

Result: Lisbon, Portugal (38.7788, -9.2558).

## Key techniques
Anchor decomposition · reverse image search (Google, Yandex, Sogou) · sign transcription · EXIF / GPS / altitude analysis · satellite and Street View verification · multi-tool corroboration

## Tools
Google Lens · Yandex Images · Sogou · ExifTool-style metadata viewers · pic2map · Picarta.ai · Google Maps / Earth / Street View
