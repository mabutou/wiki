# delete dangling images

`echo ls-la | sudo -S docker rmi -f $(echo ls-la | sudo -S docker images -f "dangling=true" -q)`

