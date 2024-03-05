# tawhiri-cookbook
A simple Cookbook to create a Tawhiri Balloon Landing Predictor

# Step 1
Clone this repo

# Step 2
Clone the Tawhiri Repo: https://github.com/limlug/tawhiri into the tawhiri-cookbook folder
# Step 3
Create folder for Open Elevation data:
  ```
  mkdir data
  ```
# Step 4
Clone the Open Elevation Repo: https://github.com/limlug/open-elevation into the tawhiri-cookbook folder

# Step 5 
Install Open Elevation data download dependencies:
  ```
  apt install unrar gdal-bin
  ```
# Step 6
Download Open Elevation data:
  ```
  ./open-elevation/create-dataset.sh
  ```
This may take a while.
# Step 7
Create folder for GRIB data:
  ```
  mkdir grib
  ```
# Step 8
Clone the Tawhiri Downloader Repo: https://github.com/balloontech/tawhiri-downloader
# Step 9
Install Tawhiri Downloader dependencies:
  ```
  apt install -y build-essential rsync git libpcre3-dev libncurses-dev pkg-config m4 unzip aspcud autoconf bubblewrap libssl-dev libgmp-dev libffi-dev libeccodes-dev libcurl4-gnutls-dev python3 python3-boto3 opam
  ```
  ```
  opam init -y
  ```
  ```
  eval $(opam env) && opam install "core=v0.14.1" async ctypes ctypes-foreign ocurl dune
  ```
# Step 10 
cd into Tawhiri Downloader Folder and build the downloader:
  ```
  cd tawhiri-downloader
  ```
  ```
  eval $(opam env) && dune build --profile=release main.exe
  ```
# Step 11
Execute GRIB downloader:
  ```
  ./_build/default/main.exe one -base-url aws-mirror -directory ../grib `date +%Y%m%d00`
  ```
This may take a while.
