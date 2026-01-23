[[build]]
```
npm run build-locale;npm run build-css;rm -rf build/; npm run build;fig build otaui; 
"OR"
npm run format;rm -rf build/; npm run build;npm run build-css; npm run build-locale;fig build otaui; 
fig kill otaui; fig rm -f otaui; fig up -d otaui;
```

```
OTA npm Start :
	samba.yml
		&kongHost kong
		  - &portalHost otaui -----> your ipAddress
		  - &portalPort 8084  -----> 3000
	compose :
		direnv allow 
		fig stop kong-configloader; fig rm -f kong-configloader; fig up -d kong-configloader;
```