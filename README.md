# PointCloud using Potree

## About LAS Files

LAS (LASer) is a file format designed for the interchange of 3-dimensional point cloud data, primarily from LiDAR (Light Detection and Ranging) systems. It is an open, binary format that stores point cloud data efficiently.

### Key Features of LAS Files:
- **Versions**: LAS 1.0 through 1.4, with 1.4 being the latest and most feature-rich.
- **Structure**:
  - **Header**: Contains metadata about the file, including version, point data format, coordinate system, and bounds.
  - **Variable Length Records (VLRs)**: Optional records for extended information like coordinate system details.
  - **Point Data Records**: The core data, each containing position (X, Y, Z), intensity, return information, classification, and more.
- **Common Attributes**:
  - **Position**: X, Y, Z coordinates (scaled and offset).
  - **Intensity**: Strength of the laser return.
  - **Return Number**: Which return this point represents (useful for vegetation analysis).
  - **Classification**: Point type (ground, vegetation, building, etc.).
  - **GPS Time**: Timestamp for each point.
  - **RGB**: Color values for photogrammetric data.
- **Compression**: LAZ is the compressed version of LAS, reducing file size significantly while maintaining full compatibility.

In this project, LAS/LAZ files are the primary input format for point cloud processing and visualization.

## For Potree

### 1. Clone and Build Potree from GitHub

```
https://github.com/potree/potree.git

```

### 2.Install dependencies

```
cd potree
npm install
```


## For PotreeConverter:

### 1. Clone and Build PotreeConverter from GitHub

```
git clone https://github.com/potree/PotreeConverter.git
cd PotreeConverter

```

### 2.Install Dependencies:

```
sudo apt install cmake gdal-bin libboost-all-dev

```

### 3. Build PotreeConverter

```
mkdir build
cd build
cmake ..
make
sudo make install

```

## 4. If not installed proper.(from PotreeConverter folder)
 ### 1. Install required dependencies
```
sudo apt update
sudo apt install -y \
cmake \
g++ \
make \
libboost-all-dev \
libgdal-dev \
libtbb-dev \
libeigen3-dev



```
### 2.Clean old build completely

```
rm -rf build
mkdir build
cd build

```
### 3.Configure with CMake

```
cmake ..

```

### 4. Build PotreeConverter

```
make -j$(nproc)

```
### 5.Verify executable exists

```
find . -name "PotreeConverter"

```

## Create Folder and add .las file in it.

## Run command for Converting .las file:(from build folder)

```
./PotreeConverter \
/mnt/c/Users/ASUS/Documents/PointCloud/data/Philadelphia_100.las \
-o /mnt/c/Users/ASUS/Documents/PointCloud/potree/pointclouds/output


```

## Start a local web server from potree folder:

```
python3 -m http.server 1234

```

### If port is busy.

#### 1.Find the process:

```
lsof -i :1234

```

#### 2. Kill it:

```
kill PID

```

#### 3. Run Finally:

```
python3 -m http.server 1234


```
