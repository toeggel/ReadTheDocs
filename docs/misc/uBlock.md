# uBlock

## Custom Block List
```  
! youtube.com##ytd-shelf-renderer.style-scope:has(span:has-text(/Related to your search/i))
! youtube.com##ytd-shelf-renderer:has-text(/People also watched/)
! youtube.com##ytd-shelf-renderer.style-scope:has(span:has-text(/Watch again/i))
! youtube.com##ytd-shelf-renderer.style-scope:has(span:has-text(/Previously watched/i))
! youtube.com##ytd-shelf-renderer.style-scope:has(span:has-text(/Learn while you're at home/i))
! youtube.com###contents > ytd-shelf-renderer:has-text(/For you/)
! youtube.com##ytd-horizontal-card-list-renderer.ytd-item-section-renderer.style-scope:has(span:has-text(/Searches related to/i))
! youtube.com##ytd-horizontal-card-list-renderer.ytd-item-section-renderer.style-scope
! youtube.com###secondary > .ytd-two-column-search-results-renderer
! youtube.com###contents > .ytd-secondary-search-container-renderer.style-scope
! youtube.com##ytd-shelf-renderer.ytd-item-section-renderer.style-scope > .ytd-shelf-renderer.style-scope
! youtube.com##ytd-shelf-renderer[thumbnail-style]


! Title:  YouTube-Cosmetic-Filters-for-uBlock-Origin - Complete version
! Description: Cosmetic filters to improve the search results, home section and video page.
! Home: https://github.com/Onsotumenh/YouTube-Cosmetic-Filters-for-uBlock-Origin

youtube.com##ytd-shelf-renderer.style-scope:has(span:has-text(/Related to your search/i))
youtube.com##ytd-shelf-renderer:has-text(/People also watched/)
youtube.com###contents > ytd-shelf-renderer:has-text(/For you/)
youtube.com##ytd-shelf-renderer.style-scope:has(span:has-text(/Watch again/i))
youtube.com##ytd-horizontal-card-list-renderer.ytd-item-section-renderer.style-scope:has(span:has-text(/Searches related to/i))
youtube.com##ytd-shelf-renderer.style-scope:has(span:has-text(/Learn while you're at home/i))
youtube.com##ytd-horizontal-card-list-renderer.ytd-item-section-renderer.style-scope
youtube.com###secondary > .ytd-two-column-search-results-renderer
youtube.com###contents > .ytd-secondary-search-container-renderer.style-scope
youtube.com##ytd-shelf-renderer.style-scope:has(span:has-text(/Previously watched/i))

! Search Results
www.youtube.com##ytd-shelf-renderer.style-scope:has(span:has-text(/For you/i))
www.youtube.com##ytd-shelf-renderer.style-scope:has(span:has-text(/People also watched/i))
www.youtube.com##ytd-shelf-renderer.style-scope:has(span:has-text(/Previously watched/i))
www.youtube.com##ytd-shelf-renderer.style-scope:has(span:has-text(/Related to your search/i))
www.youtube.com##ytd-shelf-renderer.style-scope:has(span:has-text(/Related Movies/i))
www.youtube.com##ytd-shelf-renderer.style-scope:has(span:has-text(/New for you/i))
www.youtube.com##ytd-shelf-renderer.style-scope:has(span:has-text(/Channels new to you/i))
www.youtube.com##ytd-shelf-renderer.style-scope:has(span:has-text(/Learning related/i))
www.youtube.com##ytd-shelf-renderer.ytd-item-section-renderer.style-scope:has(span:has-text(/Latest from/i))
www.youtube.com##ytd-shelf-renderer.ytd-item-section-renderer.style-scope:has(span:has-text(/Results for similar searches/i))
www.youtube.com##ytd-shelf-renderer.ytd-item-section-renderer.style-scope:has-text(/From related searches/i)
www.youtube.com##ytd-horizontal-card-list-renderer.ytd-item-section-renderer.style-scope:has-text(/People also search for/i)
www.youtube.com##ytd-horizontal-card-list-renderer.ytd-item-section-renderer.style-scope:has-text(/Searches related to/i)
www.youtube.com##ytd-movie-renderer.ytd-item-section-renderer.style-scope
www.youtube.com##ytd-reel-shelf-renderer.ytd-item-section-renderer.style-scope
!Shorts
www.youtube.com###dismissible.ytd-video-renderer.style-scope:has(ytd-thumbnail.ytd-video-renderer.style-scope:has-text(/Shorts/i))
www.youtube.com###content > .ytd-video-renderer.style-scope:has-text(/#Shorts/i)
www.youtube.com###ytd-video-renderer.ytd-item-section-renderer.style-scope:has-text(/#shorts/i)
www.youtube.com###dismissible.ytd-video-renderer.style-scope:has(.ytd-thumbnail-overlay-time-status-renderer.style-scope:has(span:has-text(/\s(0:\d\d|1:\d\d)\s/)))


! Home
www.youtube.com##contents.ytd-shelf-renderer.style-scope:has-text(/People also watched/i)
www.youtube.com##ytd-shelf-renderer.ytd-item-section-renderer.style-scope:has(span:has-text(/Watch again/i))
www.youtube.com##ytd-horizontal-card-list-renderer.ytd-item-section-renderer.style-scope:has-text(/People also watched/i)
www.youtube.com###content > .ytd-rich-section-renderer.style-scope
www.youtube.com##ytd-rich-item-renderer.ytd-rich-grid-row.style-scope > #star-survey
www.youtube.com###merch-shelf > .ytd-watch-flexy.style-scope
www.youtube.com##ytd-rich-item-renderer.ytd-rich-grid-row.style-scope > .ytd-feed-nudge-renderer.style-scope
!Shorts
www.youtube.com##ytd-rich-item-renderer.ytd-rich-grid-row.style-scope:has(span:has-text(/Shorts/i))
www.youtube.com##ytd-rich-item-renderer.ytd-rich-grid-row.style-scope:has(span:has-text(SHORTS))
www.youtube.com##ytd-rich-item-renderer.ytd-rich-grid-row.style-scope:has-text(/#Shorts/i)
! www.youtube.com##ytd-rich-item-renderer.ytd-rich-grid-row.style-scope:has(ytd-thumbnail-overlay-time-status-renderer.ytd-thumbnail.style-scope:has(span:has-text(/\s(0:\d\d|1:\d\d)\s/)))
! Keyword Bar
! www.youtube.com###scroll-container > .ytd-feed-filter-chip-bar-renderer.style-scope
! www.youtube.com###header > .ytd-rich-grid-renderer.style-scope
! Voice Search Button
www.youtube.com###voice-search-button
!shorts category
www.youtube.com##ytd-guide-entry-renderer.ytd-guide-section-renderer.style-scope > .ytd-guide-entry-renderer.style-scope.yt-simple-endpoint:has-text(/Shorts/i)

! Video Page
www.youtube.com###paid-comment-images
www.youtube.com###paid-comment-chip > .yt-pdg-comment-chip-renderer.style-scope
! www.youtube.com###comment:style(--ytd-comment-paid-background-color: red !important)
! Membership Popup
www.youtube.com###contentWrapper > .ytd-popup-container.style-scope:has(span:has-text(/Membership/i))
! Watch next / Related
www.youtube.com##ytd-item-section-renderer.ytd-watch-next-secondary-results-renderer.style-scope
! Related Keywords
www.youtube.com###content > .yt-related-chip-cloud-renderer.style-scope
! Shorts
www.youtube.com##ytd-grid-video-renderer.ytd-grid-renderer.style-scope:has(span:has-text(/Shorts/i))
www.youtube.com##ytd-grid-video-renderer.ytd-grid-renderer.style-scope:has(span:has-text(SHORTS))
www.youtube.com###contents > .ytd-item-section-renderer.style-scope:has(#title-container:has(span:has-text(/Shorts/i)))
www.youtube.com###contents > .ytd-item-section-renderer.style-scope:has(#title-container:has(span:has-text(SHORTS)))
www.youtube.com##ytd-grid-video-renderer.ytd-grid-renderer.style-scope:has(ytd-thumbnail-overlay-time-status-renderer.ytd-thumbnail.style-scope:has(span:has-text(/\s(0:\d\d|1:\d\d)\s/)))

! Optional
www.youtube.com##.ytd-button-renderer.style-scope.yt-simple-endpoint > .size-default.style-suggestive.ytd-button-renderer.style-scope
! Like/Dislike Count
www.youtube.com##ytd-toggle-button-renderer.style-text.force-icon-button.ytd-menu-renderer.style-scope > .ytd-toggle-button-renderer.style-scope.yt-simple-endpoint > .style-text.ytd-toggle-button-renderer.style-scope
! Music secondary(search results) / Related Videos(on video page)
! www.youtube.com###secondary


! Add via "https://gist.github.com/mdPlusPlus/35bee203897bed57ced1f1a5e1d2148a/raw"
! https://web.de
web.de###footer
web.de###loginsearch-ad
web.de###mainnav
web.de###promoline
web.de###rightnav
web.de##.games
web.de##.logout-modules
web.de##.partner-links
web.de##.vorteilswelt
web.de##.weather
web.de##.webcent
web.de##div.wrapper-center:nth-of-type(n+3)
web.de##.abi
web.de##tr.iba-variant-test


! https://gmx.ch
! @@||dl.gmx.ch/permission/oneTrust/live/scripttemplates/6.13.0/otBannerSdk.js$script,domain=plus.gmx.com
! ||dl.gmx.ch/uim/connector/live/v2/nonfriendlyiframe.html
! ||https://dl.gmx.ch/uim/connector/live/v2/nonfriendlyiframe.html$document 
! ||https://dl.gmx.ch/uim/connector/live/v2/nonfriendlyiframe.html$important,frame
! ##:xpath(//iframe[contains(@src, 'dl.gmx.ch/uim/connector/live/v2/nonfriendlyiframe.html')])

||dl.gmx.net/permission/live/portal/v1/ppp/core.html$subdocument
www.gmx.ch##.permission-layer-default
www.gmx.ch##.permission-core-iframe
www.gmx.ch##.ppp-layer
www.gmx.net##.ppp-layer

! 2024-04-01 https://www.postfinance.ch
www.postfinance.ch##.cookie_consent_banner--background

! Temporary
# Hide a specific channel
# www.youtube.com##ytd-video-renderer.ytd-item-section-renderer:has(a[href*="@digadigadoo6997"])

```