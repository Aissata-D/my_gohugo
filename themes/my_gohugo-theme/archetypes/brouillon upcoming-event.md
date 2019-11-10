---
title: "{{ replace .Name "-" " " | title }}"
date: {{ .Date }}
domain: son domaine
adress: son adresse
description: sa description
important: true
photos: photooo
img: 
---
cette association est....
<h4>Upcoming Events</h4>
<ul class="upcoming-events">
{{ range where .Pages.ByDate "Section" "events" }}
    {{ if ge .Date.Unix now.Unix }}
        <li>
        <!-- add span for event type -->
          <span>{{ .Type | title }} —</span>
          {{ .Title }} on
        <!-- add span for event date -->
          <span>{{ .Date.Format "2 January at 3:04pm" }}</span>
          at {{ .Params.place }}
        </li>
    {{ end }}
{{ end }}
</ul>




{{ range (( where .Site.RegularPages "Section" "events").ByParam "when") }}
    {{ if ge (Date.Format "2 January at 3:04pm" .Params.when) 
    (DateFormat "2 January at 3:04pm" now) }}
        
      <a href="{{ .Permalink}}">{{ .Params.title}}</a> <br>
      <h4>{{ .Params.label}}</h4>
      <h3>{{ Date.Format "2 January at 3:04pm" .Params.when}}</h3>
          
    {{ end }}
{{ end }}

<ul class="upcoming-events">
                {{ range where .Data.Pages.ByDate "Section" "events" }}
                  {{ if ge .Date.Unix now.Unix }}
                    <li>
                      <span>{{ .Params.when }}</span>
                      — {{ .Title }}
                    </li>
                  {{ end }}
                {{ end }}
                </ul> 




         {{ range (( where .Site.RegularPages "Section" "events").ByParam "when") }}
        {{ if ge (Date.Format "2 January at 3:04pm" .Params.when) 
        (DateFormat "2 January at 3:04pm" now) }}
            
          <a href="{{ .Permalink}}">{{ .Params.title}}</a> <br>
          <h4>{{ .Params.label}}</h4>
          <h3>{{ Date.Format "2 January at 3:04pm" .Params.when}}</h3>
              
        {{ end }}
    {{ end }}
    


           <!--           <ul><li>
                {{ range (( where .Site.RegularPages "Section" "events").ByParam "when") }}
    {{ if ge ( .Date.Format "28 January 13:05" .Params.when) ( .Date.Format "28 January 13:05" now) }}
        
      <a href="{{ .Permalink}}">{{ .Params.title}}</a> <br>
      <h4>{{ .Params.label}}</h4>
     
          
    {{ end }}
{{ end }}
          
</li></ul> --> 