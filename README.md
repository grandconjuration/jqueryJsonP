# jqueryJsonP
## Voorbeeld
https://rawgit.com/swhiteley91/jqueryJsonP/master/public_html/index.html

## Code
Hieronder zie je betreffende JQuery code om het bovenstaande te bereiken.
```javascript
    $(document).ready(function() {
        $("button").click(function(event) {
            (function() {
                var flickerAPI = "https://api.flickr.com/services/feeds/photos_public.gne?jsoncallback=?";
                $.getJSON(flickerAPI, {
                        tagmode: "any",
                        format: "json"
                    })
                    .done(function(data) {
                        $("#imagesSection").text("");
                        $.each(data.items, function(i, item) {
                            $("<section>").attr("id", "imagesSection").appendTo("#images");
                            $("<h3>").text(item.title).appendTo("#imagesSection");
                            $("<img>").attr("src", item.media.m).appendTo("#imagesSection");
                            if (i === 2) {
                                return false;
                            }
                        });
                    });
            })();
        });
    });
```

### Korte uitleg
Alle code wordt uitgevoerd onReady
```javascript
    $(document).ready(function() {
```
 Als er op de 'n button wordt gedrukt: 
```javascript
        $("button").click(function(event) {
```    
Vervolgende een anonieme functie met daarin de FlickrApi
```javascript
            (function() {
                var flickerAPI = "https://api.flickr.com/services/feeds/photos_public.gne?format=json&jsoncallback=?";
                $.getJSON(flickerAPI, {
                        tagmode: "any",
                        format: "json"
                    })
```
Zodra dat klaar is loopen we door het resultaat heen (data)
```javascript
                    .done(function(data) {
                        $("#imagesSection").text("");
                        $.each(data.items, function(i, item) {
```
Voor elke item maken we een nieuw section element, een h3 met de titel, en een img tag natuurlijk
```javascript
                            $("<section>").attr("id", "imagesSection").appendTo("#images");
                            $("<h3>").text(item.title).appendTo("#imagesSection");
                            $("<img>").attr("src", item.media.m).appendTo("#imagesSection");
                            if (i === 2) {
                                return false;
                            }
                        });
                    });
            })();
        });
    });
```

##Auteur
Simon Whiteley
