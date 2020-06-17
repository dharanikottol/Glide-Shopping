Glide Shopping allows consumers with smart phones to pull up a map pinpointing the aisleand location of the required item of their desire in a particular store.It is a mobile shopping platform that allows consumers to search, map and navigate to products in retail stores down to the sections of the aisles in which they are located. 
This solution leverages a building's existing Wi-Fi infrastructure and sensor information from mobile devices, such as data provided by the gyroscope, pedometer and compass, to deliver precise location information indoors without the need for any specialized hardware or additional infrastructure.

## Requirements (iOS)
- File `com.aisle411.venuekit.plist` bundled with your application:
```plist
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
  <key>partnerID</key>
  <string>PARTNER_ID</string>
  <key>partnerSecret</key>
  <string>PARTNER_SECRET</string>
  <key>host</key>
  <string>test.aisle411.ws</string>
</dict>
</plist>
```
- Location permissions in your `Info.plist`:
```plist
<key>NSLocationWhenInUseUsageDescription</key>
<string>Can we access your location?</string>
```

## Documentation

### Top-Level

#### Methods

- [x] `requestCachedRasterMap(args)`
  - `venueId` (Number)
  - `callback` (Callback)
- [x] `setup(args)`: This method is only applicable on Android. It must be called before any other Aisle411 module method.
  - `partnerId` (String)
  - `partnerSecret` (String)
  - `host` (String): Set to either `"production"`, `"qa"`, `"test"`, `"aisle411.ws"`, `"webservices3"`, or `"https"`.

### `MapView`
![GitHub Logo](/images/logo.png)
Format: ![Alt Text](https://www.google.com/url?sa=i&url=http%3A%2F%2Fwww.aisle411.com%2Fshops%2F&psig=AOvVaw3oDV76anvRODn7KXsI-q77&ust=1592504835496000&source=images&cd=vfe&ved=0CAIQjRxqFwoTCPjJmP28ieoCFQAAAAAdAAAAABAI)
Create a new map-view with `Aisle411.createMapView()`.

#### Properties

- [x] `url` (use the `e.path` from the `requestCachedRasterMap` callback)
- [x] `floor`
- [x] `logoPosition`
- [x] `shoppingListEnabled`
- [x] `compassEnabled`
- [x] `zoomButtonsHidden`
- [x] `zoomOnPinClickEnabled`
- [x] `mapBackgroundColor`
- [x] `selectedPinImage`
- [x] `unselectedPinImage`

#### Methods

- [x] `clear()`
- [x] `zoomIn()`
- [x] `zoomOut()`
- [x] `redraw()`
- [x] `redrawOverlay(args)`: Displays map marker pins for a given array of products. Set to empty arrays to clear the map markers.
  - `products` (Dictionary[]): Array of product configuration to be displayed. Each product dictionary must provide a `name` string field and `id` numeric field.
  - `venueItems` (Dictionary[]): Array of venue items received by the callback invoked by the  `MapView.search()` method. This array of venue item entries must pair with the given `products` array entries.
- [x] `fadeIn(args)`
  - `zoom` (Number)
  - `relativeToScreen` (Boolean)
- [x] `reloadTiles()`
- [x] `search(args)`
  - `venueId` (Number)
  - `term` (String)
  - `startingIndex` (Number): Zero based index to the first page to load.
  - `endingIndex` (Number): Zero based index to the last page to load.
  - `maxCount` (Number): Max number of items per page.
  - `callback` (Callback)

#### Events
- [x] `load`
  - Fired when a map url has been successfully loaded in the MapView.
- [x] `informationBarItemClick`
  - Fired when an item has been tapped on in the overlay product list view.
- [x] `didItemSelected`
  - Fired when a map marker pin has been tapped on and.
- [x] `didItemReselected`
  - Fired when a map marker pin that is already in the selection state has been tapped on again.
- [x] `didItemDeselected`
  - Fired when a map marker pin has been deselected. Typically happens when another pin has been tapped on.


