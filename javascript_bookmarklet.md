Javascript Bookmarlet
=====================

Create a bookmarlet with following properties :
 
Pass current URL to another using GET
    
    javascript:%20location.href='http://www.domain.com/webparser/?url='+location.href+''

Pass current URL + Title to another using GET + Open in new window

    javascript:void(window.open('http://www.domain.com/webparser/?url='+encodeURIComponent(location.href)+'&title='+encodeURIComponent(document.title)))

Clean CSS 

    javascript:(function(){var%20newSS,%20styles='*%20%20{%20background:%20white%20!%20important;%20color:%20black%20!important;%20font-family:arial,sans-serif%20!important}%20:link,%20:link%20*%20%20{%20color:%20black;#0000EE%20!important%20}%20:visited,%20:visited%20*%20%20{%20color:%20black;#551A8B%20!important%20}';%20if(document.createStyleSheet)%20%20{%20document.createStyleSheet(%22javascript:'%22+styles+%22'%22);%20}%20else%20%20{%20newSS=document.createElement('link');%20%20newSS.rel='stylesheet';%20newSS.href='data:text/css,'+escape(styles);%20%20document.getElementsByTagName(%22head%22)[0].appendChild(newSS);%20}%20})();

Clean font
    
    javascript:(function(){var%20newSS,%20styles='*%20%20{%20font-family:arial,sans-serif%20!important}';%20if(document.createStyleSheet)%20%20{%20document.createStyleSheet(%22javascript:'%22+styles+%22'%22);%20}%20else%20%20{%20newSS=document.createElement('link');%20%20newSS.rel='stylesheet';%20newSS.href='data:text/css,'+escape(styles);%20%20document.getElementsByTagName(%22head%22)[0].appendChild(newSS);%20}%20})();
