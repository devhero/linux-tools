### Finding the process that is using a certain port in Linux
  https://superuser.com/questions/42843/finding-the-process-that-is-using-a-certain-port-in-linux#42849

    lsof -i tcp:80

  will give you the list of processes using tcp port 80.

  Alternatively,

    sudo netstat -nlp

