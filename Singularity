Bootstrap: library
From: ubuntu

%help
    #comments/helpful hints
    Test Singularity Container with a Hello World Python Script

%labels
    #metadata within container
    Creator Liberty

%environment
    #export MY_VAR=’~~~~  This is my environment variable ~~~~’

%files
    #allows us to copy files into our container
    #FILE_NAME DIRECTOR
    helloWorld.py /
    #
    
    helloWorld.py ~/

%test
grep -q NAME=\"Ubuntu\" /etc/os-release
    if [ $? -eq 0 ]; then
        echo "Container base is Ubuntu as expected."
    else
        echo "Container base is not Ubuntu."
    fi

%post
    #add packages
    sed -i 's/security/old-releases/g' /etc/apt/sources.list && \
    sed -i 's/archive/old-releases/g' /etc/apt/sources.list && \
    sed -i 's/cosmic-old-releases/cosmic/g' /etc/apt/sources.list && \
    apt-get update && \
    apt-get install -y vim && \
    apt-get install -y python3

%runscript
    #echo "Container was created $NOW"
    #cat /etc/lsb-release
    python3 /helloWorld.py