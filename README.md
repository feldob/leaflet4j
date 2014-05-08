leaflet4j
=========

Leaflet Demo[http://leafletjs.com/examples/quick-start.html] rewritten to Java via DukeScript[http://html.java.net]. Clone and then:

$ mvn clean install exec:java

to see the application. Check Main.java to see the initialization which basically consists of:

    public static void onPageLoad(String... args) throws Exception {
        final Leaflet map = Leaflet.map("map");
        map.setView(new LatLng(51.505, -0.09), 13);
        map.addTileLayer(
            "https://{s}.tiles.mapbox.com/v3/{id}/{z}/{x}/{y}.png",
            "Map data &copy; <a href='http://openstreetmap.org'>OpenStreetMap</a> contributors, " +
            "<a href='http://creativecommons.org/licenses/by-sa/2.0/'>CC-BY-SA</a>, " +
            "Imagery © <a href='http://mapbox.com'>Mapbox</a>",
            18,
            "examples.map-9ijuk24y"
        );
        map.addCircle(
            new LatLng(51.508, -0.11), 500, "red", "#f03", 0.5
        ).bindPopup("I am a circle");
        map.addPolygon(
            new LatLng(51.509, -0.08),
            new LatLng(51.503, -0.06),
            new LatLng(51.51, -0.047) 
        ).bindPopup("I am a polygon");

        map.on(MouseEvent.Type.CLICK, new MouseListener() {
            @Override
            public void onEvent(MouseEvent ev) {
                map.openPopup(ev.getLatLng(), "You clicked the map at " + ev.getLatLng());
            }
        });
    }
