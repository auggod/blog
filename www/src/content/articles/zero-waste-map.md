---
date: 2019-01-31T10:18:00-00:00
description: "Zero Waste Map manifesto, api and more..."
featured_image: "/images/map.jpg"
title: "Zero Waste Map"
toc: true
---

{{< image webp="/images/zerowastemap.webp" jpeg="/images/zerowastemap.jpg" src="/images/zerowastemap.jpg" alt="Screenshot map" >}}

https://zerowastemap.app (opening soon)

## Manifesto (draft)

**Zero Waste Map** is for all independantly or co-owned structures that apply to the zero waste movement.

Substantial quantity of goods available in bulk (**stored in jars, tanks and others containers**) is a **required** condition for grocery stores, markets, coops to appear on the map.

Absense of disposable plastic bags and being **100% zerowaste friendly** is required too.

Some stores will still appear on the map even though they still sell a lot of goods wraped in plastic (often meats and some dried goods) as long as long as other conditions are met.

Selling any goods wrapped in plastic is heavily discouraged and will cause store to be flagged as not being 100% zero waste. (ex: farmcoop)

Providing only bio labelled products is **not required** but is considered **best practice**.

Often, best solutions are found by simply looking at how we did in the past. Fortunately, artisans are coming back in our cities.

- **Zero Waste Friendly**

    Allow people to bring their own containers or allow them to not use any container.
    Example: Eggs available per piece. (~ 0,40 €)

## YAZWM ?

### Yet Another Zero Waste Map ?

I've started this project as an experiment in mid 2017. I got into other projects in 2018 and I got back at it late 2018.
The initial concept didn't evolve much. I'm happy with it.

Important points for this project are

- Open source (front end code, backend code, icons)
    - Open Street Map (using leaflet.js)
    - Google free
    - Looking to implement geocoding with mapzen (linux foundation backed) instead of mapbox)
- Performance
- Multilingual (fr, nl, de, en, ...)

## Zero Waste Map API (sample)

### Locate

GET [/api/locate?longitude=4&latitude=50&radius=50&country=BE](https://zerowastemap.app/api/locate?longitude=4&latitude=50&radius=50&country=BE)

### Add a location (See [schemas](https://github.com/zerowastemap/schemas))

POST `/api/locations`

A token is needed

{{< highlight javascript>}}
{
  name: 'Original Unverpackt',
  geometry: {
    coordinates: [52.5069312, 13.1445476],
    type: 'Point'
  },
  address: {
    streetName: 'Wiener Straße',
    streetNumber: '16',
    countryCode: 'DE',
    city: 'Berlin',
    zip: '10999'
  },
  fullAddress: 'Wiener Straße 16, 10999 Berlin, Allemagne',
  tags: ['bio', 'bulk'],
  email: 'kontakt@original-unverpackt.de',
  rating: 5,
  price: 3,
  url: 'https://original-unverpackt.de/',
  image: {
    src: 'https://static.zerowastemap.app/file/zerowastemap/1928699b-410a-4e70-8ccd-eba63b174ffe',
    uuid: '1928699b-410a-4e70-8ccd-eba63b174ffe'
  },
  note: `
    Amazing place!
  `,
  kind: 'supermarket'
}
{{< / highlight >}}

### GeoJSON

[GeoJSON](http://geojson.org/) is a format for encoding a variety of geographic data structures.

Here's a sample object.

{{< highlight json>}}
{
  "type": "Feature",
  "geometry": {
    "coordinates": [
      4.344716,
      50.832396
    ],
    "type": "Point"
  },
  "properties": {
    "address": {
      "zip": "1060",
      "countryCode": "BE"
    },
    "description": null,
    "email": "anne@alimentationgeniale.be",
    "kind": "market",
    "fullAddress": "1, Avenue de la Porte de Hal 1060 Saint-Gilles, Belgique",
    "image": {
      "width": 2048,
      "height": 2048,
      "uuid": "0b7267bb-a245-4b34-a342-87da245f4d5d",
      "src": "https://static.zerowastemap.app/file/zerowastemap/0b7267bb-a245-4b34-a342-87da245f4d5d"
    },
    "name": "Alimentation Géniale",
    "price": 3,
    "rating": 5,
    "tags": [
      "bio"
    ],
    "url": "alimentationgeniale.be"
  }
}
{{< / highlight >}}

### Token

A token is sometimes needed to perform requests.
An anonymous token with limited capabilities is provided for apps to communicate with api.

It’s recommended to get a token for your app so we can identify you.

## A tool for collaboration

### Anyone can add points

Before being added to the map, points will need to be approved by staff or a trusted member, otherwise community will need to vote.

### Verification

People can register and claim data points associated with their email address.

## In Common

{{< image webp="/images/incommon.webp" png="/images/incommon.png" src="/images/incommon.png" width="144" alt="Incommon.cc logo" >}}

[InCommon.cc](https://incommon.cc) is an effort to generate an infrastructure for mapping the commons. Using free software and open data, the effort aims to gather commons initiatives around a set of tools suitable to identify, promote, and defend the commons. Discuss the plans and development and join a growing community of grassroots initiatives for the commons.

## Hosting

Though subject. At the moment, I use [now.sh](https://now.sh) by [zeit.co](https://zeit.co) for hosting front end and api's ([node.js](https://node.js)). I'll be very happy if they launch a self hosted kind of now.sh.

A first mongodb instance (database) will be hosted on a [gandi](https://gandi.net) server located in Luxembourg.

I use cloudflare, especially for interop with backblaze (to store static content).

## Domain name

`zerowastemap.app` has been chosen instead of `depackt.be` which was the first domain I bought for the project. I didn't like it that much.
