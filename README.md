# Resources for Induction

Here is a set of resources that will help you out to learn and explore the various topics going to be taught in your induction. This is not exhaustive, and will keep on updating as we continue with the induction.

## 1) Standard Template Library (STL)

STL is a library in C++ which allows you to make use of various data structures and algorithms (DSA), without having to implement them yourself.

There are a lot of DSAs that are part of this.

- Get started: [here](https://www.youtube.com/watch?v=ltBdTiRgSaw)

> This will introduce you to the basics of how to get started with STL

- [Geeks for Geeks](https://www.geeksforgeeks.org/cpp-stl-tutorial/)

> Once you are done, you can get started with these. This is a compilation of most of the DSAs in STL.

## 2) Object Oriented Programming (OOPs)

- A good [introduction](https://www.w3schools.com/cpp/cpp_oop.asp)

## 3) OpenCV

### Installation

- Enter the following command in the terminal

```bash
sudo apt install libopencv-dev python3-opencv
```

- You will also need CMake,a build utility. It helps you link different cpp and hpp files, without much hassle, especially as your project grows larger.

```bash
sudo apt-get install build-essential libssl-dev
cd /tmp
wget https://github.com/Kitware/CMake/releases/download/v3.20.0/cmake-3.20.0.tar.gz
tar -zxvf cmake-3.20.0.tar.gz
cd cmake-3.20.0
./bootstrap
make
sudo make install
```

For creating any starter folder,

- Create a folder, and go inside it. This will be your root folder.
- Create your cpp file, let's say, `file_name.cpp`
- Create a file called CMakeLists.txt
- Create a folder called bin

Put this basic Video Capture from WebCam code in `file_name.cpp`

```cpp
#include <opencv2/opencv.hpp>
#include <iostream>

int main()
{
    cv::Mat myImage;
    cv::namedWindow("Video Player");
    cv::VideoCapture cap(0);
    if (!cap.isOpened()) {
        std::cerr << "No video stream detected" << std::endl;
        system("pause");
        return -1;
    }
    while (true) {
        cap >> myImage;
        if (myImage.empty())
            break;
        imshow("Video Player", myImage);
        char c = (char)cv::waitKey(25);
        if (c == 27)
            break;
    }
    cap.release();
    return 0;
}
```

Put this file content inside the `CMakeLists.txt`

```c
cmake_minimum_required(VERSION 2.8)
PROJECT(OPENCV)
find_package(OpenCV REQUIRED)
include_directories( ${OPENCV_INCLUDE_DIRS} )
add_executable(bin/file_name file_name.cpp)
target_link_libraries(bin/file_name ${OpenCV_LIBS})
```

Replace `file_name` with your cpp file name.

Now you should have a directory/folder with these files:

```bash
.
├── bin
├── CMakeLists.txt
└── your_file_name.cpp
```

Now to build the cpp files you have,
Type the following commands:

```bash
cmake . # to create CMake build files
make # to build your cpp files/project, according to the build files made above
```

You'll now have the binary of your cpp file within ./bin
To run it:

```./bin/your_file_name```

You should see a window pop up with your camera feed.

### Resources

- As always, the Documentation is always good, but way too general: [here](https://docs.opencv.org/4.2.0/d1/dfb/intro.html)

- Introduction: [C++](https://github.com/murtazahassan/Learn-OpenCV-cpp-in-4-Hours) and [Python](https://www.youtube.com/watch?v=WQeoO7MI0Bs)

> Pretty long. Recommended to look a the code given and see the end products. You can skip over the part where the code is being written. Don't worry, it won't take more than 2 hours to familiarize yourself

- Knowing the concepts always helps: [Theory](https://web.stanford.edu/class/ee368/handouts.html)

> This is optional.

- Once you are familiar with this, moving on to solving some [examples](!!!!!!)
