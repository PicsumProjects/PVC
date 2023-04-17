# Spec

## A frame

One frame is defined with the layout (in little endian):

Width (Positive integer less than 65536 or 0 with the size of 2 bytes)

Height (Positive integer less than 65536 or 0 with the size of 2 bytes)

Start time in milliseconds (Positive integer less than 4294967296 or 0 with the size of 2 bytes)

Data length (Positive integer less than 18446744073709551616, or 0 meaning the length of the compressed form of the data in the frame)

Data (The data size is defined as the `Width` property × the `Height` property × the stride of the pixel format, described in the container format, and the form of encoding the data is by subtracting each data byte of the data from the prevvious frame, which if the previous frame does not include that pixel or the previous frame does not exist, then no filter is applied. The data is subtraced from the raw data of the previous frame. Once that is done, LZ4 compression is applied.)

## The codec format

The codec format is described as data of all of the frames in the video concatenated.
