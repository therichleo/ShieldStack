in first we have to go to grafana.ini file
you know with find -name "granafa.ini" we can search and go to the "features_toggles" with ctrl+W
in that place we have to make sure we have canvasPanelPanZoom = true allowed, if we dont have this, we need to put this

so it should look like this
<img width="1684" height="844" alt="Image" src="https://github.com/user-attachments/assets/7b9e74b2-0b24-4e47-afe1-a504d5fb518c" />

after we need to restart grafana with this command: ..

and now if we go to the grafana and put canvas panel

<img width="1548" height="836" alt="Image" src="https://github.com/user-attachments/assets/8106d3be-e63b-4ed4-a358-c9e79f492e5c" />

in the canvas options we have the pan and zoom option.