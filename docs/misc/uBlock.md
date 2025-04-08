# uBlock

## Custom uBlock filter list
```  
! Title:  YouTube-Cosmetic-Filters-for-uBlock-Origin - Complete version
! Description: Cosmetic filters to improve the search results, home section and video page.
! Home: https://github.com/Onsotumenh/YouTube-Cosmetic-Filters-for-uBlock-Origin

! Search Results
www.youtube.com##ytd-shelf-renderer.style-scope:has(span:has-text(/For you/i))
www.youtube.com##ytd-shelf-renderer.style-scope:has(span:has-text(/People also watched/i))
www.youtube.com##ytd-shelf-renderer.style-scope:has(span:has-text(/Previously watched/i))
www.youtube.com##ytd-shelf-renderer.style-scope:has(span:has-text(/Related to your search/i))
www.youtube.com##ytd-shelf-renderer.style-scope:has(span:has-text(/Related Movies/i))
www.youtube.com##ytd-shelf-renderer.style-scope:has(span:has-text(/New for you/i))
www.youtube.com##ytd-shelf-renderer.style-scope:has(span:has-text(/Channels new to you/i))
www.youtube.com##ytd-shelf-renderer.style-scope:has(span:has-text(/Related chapters/i))
www.youtube.com##ytd-shelf-renderer.ytd-item-section-renderer.style-scope:has(span:has-text(/Latest from/i))
www.youtube.com##ytd-shelf-renderer.ytd-item-section-renderer.style-scope:has(span:has-text(/Results for similar searches/i))
www.youtube.com##ytd-shelf-renderer.ytd-item-section-renderer.style-scope:has-text(/From related searches/i)
www.youtube.com##ytd-horizontal-card-list-renderer.ytd-item-section-renderer.style-scope:has-text(/People also search for/i)
www.youtube.com##ytd-horizontal-card-list-renderer.ytd-item-section-renderer.style-scope:has-text(/Searches related to/i)
www.youtube.com##ytd-horizontal-card-list-renderer.ytd-item-section-renderer.style-scope:has-text(/Related chapters/i)
www.youtube.com##ytd-movie-renderer.ytd-item-section-renderer.style-scope
www.youtube.com##ytd-reel-shelf-renderer.ytd-item-section-renderer.style-scope
www.youtube.com##ytd-shelf-renderer.ytd-item-section-renderer.style-scope:has-text(/Latest Posts From/i)
www.youtube.com###about-these-results
www.youtube.com##.ytd-item-section-renderer.style-scope > .ytd-ad-slot-renderer.style-scope
! Crisis Resource Panel
www.youtube.com##ytd-emergency-onebox-renderer.ytd-item-section-renderer.style-scope > .ytd-emergency-onebox-renderer.style-scope
!Shorts
www.youtube.com###shorts-container
www.youtube.com###dismissible.ytd-video-renderer.style-scope:has(ytd-thumbnail.ytd-video-renderer.style-scope:has-text(/Shorts/i))
www.youtube.com###content > .ytd-video-renderer.style-scope:has-text(/#Shorts/i)
www.youtube.com###ytd-video-renderer.ytd-item-section-renderer.style-scope:has-text(/#shorts/i)

! Home
www.youtube.com##contents.ytd-shelf-renderer.style-scope:has-text(/People also watched/i)
www.youtube.com##ytd-shelf-renderer.ytd-item-section-renderer.style-scope:has(span:has-text(/Watch again/i))
www.youtube.com##ytd-horizontal-card-list-renderer.ytd-item-section-renderer.style-scope:has-text(/People also watched/i)
www.youtube.com###content > .ytd-rich-section-renderer.style-scope
www.youtube.com##ytd-rich-item-renderer.ytd-rich-grid-row.style-scope > #star-survey
www.youtube.com###merch-shelf > .ytd-watch-flexy.style-scope
www.youtube.com##ytd-rich-item-renderer.ytd-rich-grid-row.style-scope > .ytd-feed-nudge-renderer.style-scope
www.youtube.com##ytd-rich-item-renderer.style-scope > .ytd-feed-nudge-renderer.style-scope
www.youtube.com##.ytd-rich-item-renderer.style-scope > .ytd-feed-nudge-renderer.style-scope
www.youtube.com##ytd-mini-guide-entry-renderer.ytd-mini-guide-renderer.style-scope
!Shorts
www.youtube.com##ytd-rich-item-renderer.ytd-rich-grid-row.style-scope:has(span:has-text(/Shorts/i))
www.youtube.com##ytd-rich-item-renderer.ytd-rich-grid-row.style-scope:has(span:has-text(SHORTS))
www.youtube.com##ytd-rich-item-renderer.ytd-rich-grid-row.style-scope:has-text(/#Shorts/i)
! Reduce empty slots in grid
youtube.com##ytd-rich-grid-row,#contents.ytd-rich-grid-row:style(display: contents !important)

! Keyword Bar (removes "sort by" on video page)
! www.youtube.com###scroll-container > .ytd-feed-filter-chip-bar-renderer.style-scope
! www.youtube.com###header > .ytd-rich-grid-renderer.style-scope
! Voice Search Button
www.youtube.com###voice-search-button
!shorts category
www.youtube.com##ytd-guide-entry-renderer.ytd-guide-section-renderer.style-scope > .ytd-guide-entry-renderer.style-scope.yt-simple-endpoint:has-text(/Shorts/i)

! Video Page
www.youtube.com###paid-comment-images
www.youtube.com###paid-comment-chip > .yt-pdg-comment-chip-renderer.style-scope
www.youtube.com###paid-comment-background
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

! Optional
www.youtube.com##.ytd-button-renderer.style-scope.yt-simple-endpoint > .size-default.style-suggestive.ytd-button-renderer.style-scope
! Like/Dislike Count
www.youtube.com##ytd-toggle-button-renderer.style-text.force-icon-button.ytd-menu-renderer.style-scope > .ytd-toggle-button-renderer.style-scope.yt-simple-endpoint > .style-text.ytd-toggle-button-renderer.style-scope
! Music secondary(search results)
www.youtube.com###contents > .ytd-secondary-search-container-renderer.style-scope
! Premium Videos
www.youtube.com##ytd-rich-item-renderer.ytd-rich-grid-row.style-scope > .ytd-rich-item-renderer.style-scope:has(.ytd-rich-grid-media.style-scope.video-badge:has-text(Premium))
! Time Based Shorts Filters
  ! Search Results
www.youtube.com###dismissible.ytd-video-renderer.style-scope:has(.ytd-thumbnail-overlay-time-status-renderer.style-scope:has(span:has-text(/\s(0:\d\d|1:\d\d)\s/)))
www.youtube.com###dismissible.ytd-video-renderer.style-scope:has(.ytd-thumbnail-overlay-time-status-renderer.style-scope:has-text(/\s(0:\d\d|1:\d\d)\s/))
  ! Home
www.youtube.com##ytd-rich-item-renderer.ytd-rich-grid-row.style-scope:has(ytd-thumbnail-overlay-time-status-renderer.ytd-thumbnail.style-scope:has(span:has-text(/\s(0:\d\d|1:\d\d)\s/)))
  ! Video Page
www.youtube.com##ytd-grid-video-renderer.ytd-grid-renderer.style-scope:has(ytd-thumbnail-overlay-time-status-renderer.ytd-thumbnail.style-scope:has(span:has-text(/\s(0:\d\d|1:\d\d)\s/)))


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