This error appears when you run the docker and this exited automatically and its in the column of CREATED of docker with the command ```docker ps -a```

We saw "(137) Exited"

So this error is common, but his fix is not easy to know

- in the first we go to the terminal and put ```find -name "jvm.options ``` and have to go to that file
<img width="1540" height="136" alt="Image" src="https://github.com/user-attachments/assets/782ce2d3-ba7d-418d-9865-656aba409f37" />
- 
and we have to copy al off the text that I show
then we quit and go to jvm.options.d
and enter to nano jvm.options
<img width="1524" height="130" alt="Image" src="https://github.com/user-attachments/assets/e8968539-ed14-478a-8939-cfc37fa77116" />
then we have to put that we copy in this file, and edit with the line


Xms4g to Xms1g

<img width="946" height="536" alt="Image" src="https://github.com/user-attachments/assets/cc949d26-c37b-43b1-8bb3-54dda94981d5" />

and this problem is solved