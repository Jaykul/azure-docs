---
title: Show information about a coordinate with Azure Maps | Microsoft Docs
description: How to display information about an address on the map when a user selects a coordinate
author: jingjing-z
ms.author: jinzh
ms.date: 11/15/2018
ms.topic: conceptual
ms.service: azure-maps
services: azure-maps
manager: 
ms.custom: codepen
---

# Get information from a coordinate

This article shows how to make a reverse address search that shows the address of a clicked popup location.

There are two ways to make a reverse address search. One way is to query the [Azure Maps Reverse Address Search API](https://docs.microsoft.com/rest/api/maps/search/getsearchaddressreverse) through a service module. The other way is to make a [XMLHttpRequest](https://xhr.spec.whatwg.org/) to the API to find an address. Both ways are surveyed below.

## Make a reverse search request via service module

<iframe height='500' scrolling='no' title='Get information from a coordinate (Service Module)' src='//codepen.io/azuremaps/embed/ejEYMZ/?height=265&theme-id=0&default-tab=js,result&embed-version=2&editable=true' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='https://codepen.io/azuremaps/pen/ejEYMZ/'>Get information from a coordinate (Service Module)</a> by Azure Maps (<a href='https://codepen.io/azuremaps'>@azuremaps</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>

The first block of code constructs a Map object. You can see [create a map](./map-create.md) for instructions.

The line in the second block of code instantiates a client service.

The third block of code updates the style of mouse cursor to a pointer and [popup](https://docs.microsoft.com/javascript/api/azure-maps-control/atlas.popup?view=azure-iot-typescript-latest#open) object. You can see [add a popup on the map](./map-add-popup.md) for instructions.

The fourth block of code adds an [event listener](https://docs.microsoft.com/javascript/api/azure-maps-control/atlas.map?view=azure-iot-typescript-latest#events) for mouse clicks. Upon a mouse click, it creates a search query with the coordinates of the clicked point. It then uses the map's [getSearchAddressReverse](https://docs.microsoft.com/javascript/api/azure-maps-rest/atlas.service.models.searchgetsearchaddressreverseresponse?view=azure-iot-typescript-latest) endpoint to query the address for the coordinates.

For a successful response, it collects the address for the clicked location, and defines the popup content and position via [setOptions](https://docs.microsoft.com/javascript/api/azure-maps-control/atlas.popup?view=azure-iot-typescript-latest#setoptions-popupoptions-) function of the popup class.

The change of cursor, a popup object, and the click event are all created in the map's [load event listener](https://docs.microsoft.com/javascript/api/azure-maps-control/atlas.map?view=azure-iot-typescript-latest#events) to ensure map loads fully before the coordinates information can be retrieved.

## Make a reverse search request via XMLHttpRequest

<iframe height='500' scrolling='no' title='Get information from a coordinate' src='//codepen.io/azuremaps/embed/ddXzoB/?height=516&theme-id=0&default-tab=js,result&embed-version=2&editable=true' frameborder='no' allowtransparency='true' allowfullscreen='true' style='width: 100%;'>See the Pen <a href='https://codepen.io/azuremaps/pen/ddXzoB/'>Get information from a coordinate</a> by Azure Maps (<a href='https://codepen.io/azuremaps'>@azuremaps</a>) on <a href='https://codepen.io'>CodePen</a>.
</iframe>

The first block of code above constructs a Map object. You can see [create a map](./map-create.md) for instructions.

The second block of code updates the style of mouse cursor to a pointer and [popup](https://docs.microsoft.com/javascript/api/azure-maps-control/atlas.popup?view=azure-iot-typescript-latest#open) object. You can see [add a popup on the map](./map-add-popup.md) for instructions.

The third block of code adds an event listener for mouse clicks. Upon a mouse click, it sends an [XMLHttpRequest](https://xhr.spec.whatwg.org/) to [Azure Maps Reverse Address Search API](https://docs.microsoft.com/rest/api/maps/search/getsearchaddressreverse) to query for the clicked coordinates address. For a successful response, it collects the address for the clicked location, and defines the popup content and position via [setOptions](https://docs.microsoft.com/javascript/api/azure-maps-control/atlas.popup?view=azure-iot-typescript-latest#setoptions-popupoptions-) function of the popup class.

The change of cursor, a popup object, and the click event are all created in the map's [load event listener](https://docs.microsoft.com/javascript/api/azure-maps-control/atlas.map?view=azure-iot-typescript-latest#events) to ensure map loads fully before the coordinates information can be retrieved.

## Next steps

Learn more about the classes and methods used in this article:

> [!div class="nextstepaction"]
> [Map](https://docs.microsoft.com/javascript/api/azure-maps-control/atlas.map?view=azure-iot-typescript-latest)

> [!div class="nextstepaction"]
> [Popup](https://docs.microsoft.com/javascript/api/azure-maps-control/atlas.popup?view=azure-iot-typescript-latest)

See the following articles for full code examples:

> [!div class="nextstepaction"]
> [Show directions from A to B](./map-route.md)

> [!div class="nextstepaction"]
> [Show traffic](./map-show-traffic.md)
