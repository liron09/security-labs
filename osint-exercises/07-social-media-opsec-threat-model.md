# Case Study: How Social Media Enables Physical Crime (OPSEC Threat Model)

**Type:** Threat modeling / OPSEC · **Program:** OSINT Analyst Program (Reichman University & Google)

## Scenario
A high-profile person's rented villa in Mykonos was burglarized while the group was out on a day trip. The burglars had followed the group's social media. I analyzed, from the attacker's perspective, how open sources enabled the crime, then wrote defensive recommendations.

## 1. Knowing when the villa is empty
- **Real-time stories:** friends posted live stories tagging the whole group at a remote location, which confirmed the property was empty.
- **Pattern of life:** following the accounts revealed the vacation dates and daily routine.

## 2. Narrowing down the villa: funnel approach
Visual anchors leaked in the stories: a turquoise private pool, a 3-storey façade, a distinctive living room and mountains in the background.
1. **Terrain matching:** match the skyline to the real topography in Google Earth Pro (line of sight), narrowing to a stretch of coast.
2. **Platform enumeration:** filter Airbnb/Booking listings ("Mykonos villa, private pool, 3 floors") and match listing photos to the stories.
3. **Component reverse search:** crop unique architectural details and run them through Google Lens and Yandex to find other guests' geotagged photos.

## 3. Estimating the target's value
Brand analysis of visible luxury items, lifestyle indicators (villa, restaurants, flights) and social-circle analysis (traveling with public figures and businesspeople).

## 4. Methodology for profiling a public figure
Digital footprint mapping, including the **second circle** (family and friends often leak more), historical pattern-of-life analysis, and asset identification from background details.

## 5. Mitigation recommendations
- **Delayed posting:** publish only after leaving the location. This was the key lesson of the incident.
- **Circle discipline:** brief everyone in the group not to geotag or tag the principal in real time.
- **Visual OPSEC:** avoid images that expose a distinctive façade, interior or skyline.
