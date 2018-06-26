<p align="center">
  <a href="https://github.com/adamfaliq42/jivesearch/edit/master/README.md">
    <img alt="jive-search logo" src="frontend/static/icons/logo.png">
  </a>
</p>

<br>


<p align="center">
Jive Search is the open source search engine that does not track you. Pages are ranked based on their upvotes. Search privately, now : https://www.jivesearch.com
</p>

<br>

<p align="center">
   <a href="https://github.com/jivesearch/jivesearch"><img src="https://img.shields.io/badge/go-1.10.2-blue.svg"></a>
   <a href="https://travis-ci.org/jivesearch/jivesearch"><img src="https://travis-ci.org/jivesearch/jivesearch.svg?branch=master"></a>
  <a href="https://github.com/jivesearch/jivesearch/blob/master/LICENSE"><img src="https://img.shields.io/badge/license-Apache-brightgreen.svg"></a>
</p>

<br>
 
## 🚩Table of Contents
- [Browser Support](#browser-support)
- [Quick start](#quick-start)
- [Installation](#installation)
- [Status](#status)
- [Roadmap](#roadmap)
- [Bugs and feature requests](#bugs-and-feature-requests)
- [Documentation](#documentation)
- [Contributing](#contributing)
- [Community](#community)
- [Creators](#creators)
- [Copyright and license](#copyright-and-license)


<br>


## 🌏 Browser Support
| <img src="https://user-images.githubusercontent.com/1215767/34348387-a2e64588-ea4d-11e7-8267-a43365103afe.png" alt="Chrome" width="16px" height="16px" /> Chrome | <img src="https://user-images.githubusercontent.com/1215767/34348590-250b3ca2-ea4f-11e7-9efb-da953359321f.png" alt="IE" width="16px" height="16px" /> Internet Explorer | <img src="https://user-images.githubusercontent.com/1215767/34348380-93e77ae8-ea4d-11e7-8696-9a989ddbbbf5.png" alt="Edge" width="16px" height="16px" /> Edge | <img src="https://user-images.githubusercontent.com/1215767/34348394-a981f892-ea4d-11e7-9156-d128d58386b9.png" alt="Safari" width="16px" height="16px" /> Safari | <img src="https://user-images.githubusercontent.com/1215767/34348383-9e7ed492-ea4d-11e7-910c-03b39d52f496.png" alt="Firefox" width="16px" height="16px" /> Firefox |
| :---------: | :---------: | :---------: | :---------: | :---------: |
| Yes | 10+ | Yes | Yes | Yes |


<br>
  

## 🐾 Quick Start
1. Go to Jive Search's [homepage](https://www.jivesearch.com).
2. Start searching.
3. Upvote or downvote the pages!


<br>

## 💾 Installation
The below will build and run a Docker Compose file for Elasticsearch, OpenResty (Nginx), PostgreSQL, Redis, and a NSFW/image classification server. The OpenResty build assumes you have a domain name as well as a Let's Encrypt SSL certificate. However, in order for the nginx.conf file to dynamically load your SSL certificate you will need to create a symlink to a generic "domain" folder (replace "example.com" with your domain). For local development you can skip this step.

```bash
$ ln -s /etc/letsencrypt/live/example.com /etc/letsencrypt/live/domain
```

Install and run

```bash
$ go get -u github.com/jivesearch/jivesearch
$ cd $GOPATH/src/github.com/jivesearch/jivesearch/docker
$ domain=example.com && data_directory=/path/to/data && sudo mkdir -p $data_directory/elasticsearch && sudo chown 1000:1000 $data_directory/elasticsearch && sudo DATA_DIRECTORY=$data_directory ES_HEAP=2g NGINX_DOMAIN=$domain docker-compose up
```

Elasticsearch may give you an error about max virtual memory areas. In that case:
```bash
$ sudo sysctl -w vm.max_map_count=262144
```

For systemd settings (replace "myuser" below and edit env variables as needed):
```bash
sudo curl -o /etc/systemd/system/crawler.service https://gist.githubusercontent.com/brentadamson/0880ef548130f69c2537049a550be8e8/raw/42269dfcba6d86aba49bc56ffa7e60a9eb7ebdf3/crawler
```
```bash
sudo curl -o /etc/systemd/system/frontend.service https://gist.githubusercontent.com/brentadamson/7b8117347909cc38384fed589a3d785d/raw/1a0f14f7a8e61abd007224b3f0937e62e344a3e5/frontend
```

##### Wikipedia Dump File
```bash
$ cd $GOPATH/src/github.com/jivesearch/jivesearch/instant/wikipedia/cmd/dumper && go run dumper.go --workers=3 --dir=/path/to/wiki/files --text=true --data=true --truncate=400
```
##### MusicBrainz
Instructions for MusicBrainz (to show the album discography instant answer) can be found [here](https://gist.github.com/brentadamson/b711d5c9c4d974d6999876004f8bc1cd).

<br>


## 🚀 **Roadmap** 
### Our goal is to create a search engine that respects your privacy AND delivers great search results, instant answers, maps, image search, news, and more. 
  
Marked items indicate progress has been made in that category. There is much more to do in each area. Suggestions are welcome!
- [x] Privacy
- [x] !Bangs
- [x] Core Search Results & Distributed Crawler
    - [x] Language & Region
    - [ ] Advanced Search (exact phrase, dogs OR cats,  -cats, site/domain search, etc.)
    - [ ] Filetype
    - [ ] SafeSearch        
    - [ ] Time Search (past year/month/day/hour, etc.
- [x] Autocomplete
- [ ] Phrase Suggester (a.k.a. "Did You Mean?")
- [x] Instant Answers
    - [x] Birthstone, camelcase, characters, coin toss, frequency, POTUS, prime, random, reverse, stats, user agent, etc. 
    - [x] Discography/Music albums
    - [x] JavaScript-based answers
        - [x] Basic calculator
            - [ ] Mortgage, financial and other calculators
        - [x] CSS/JavaScript/JSON/etc minifier and prettifier
        - [x] Converters (meters to feet, mb to gb, etc...)
    - [x] Package Tracking (UPS, FedEx, USPS, etc...)
    - [x] Stack Overflow
    - [x] Stock Quotes & Charts    
    - [x] Weather
    - [x] Wikipedia summary
    - [x] Wikidata answers (how tall is, birthday, etc.)
    - [x] Wikiquote
    - [x] Wiktionary    
    - [ ] Many more instant answers (including from 3rd party APIs)
    - [ ] Translate trigger words and answers to other languages?
- [ ] Maps
- [ ] Image Search
- [ ] Video Search
- [ ] Flight Info & Status
- [ ] News
- [ ] Shopping
- [ ] Custom Themes

- [ ] New name/ logo
- [ ] Documentation
    - [ ] Translate to Chinese, French and other languages
    - [ ] How does Jive Search work? (link to /about page)
    - [ ] How do we take care of privacy?
    - [ ] Test and benchmark

<br>

## 📙 Documentation
Jive Search's documentation is hosted on GoDoc Page [here](https://godoc.org/github.com/jivesearch/jivesearch).

<br>

## 💬 Contributing
Want to contribute? Great! 

Search for existing and closed issues. If your problem or idea is not addressed yet, please open a new issue [here](https://github.com/jivesearch/jivesearch/issues/new).

You can also join us in our chatroom at https://discord.gg/cfxQkuh.

<br>

## 📜 Copyright and License
Code and documentation copyright 2018 the [Jivesearch Authors](https://github.com/jivesearch/jivesearch/graphs/contributors). Code and docs released under the [Apache License](https://github.com/jivesearch/jivesearch/blob/master/LICENSE).
