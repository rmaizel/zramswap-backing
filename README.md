# ZRAMSWAP-BACKING

These files can be used to replace the existing `zramswapon` and `zramswapoff` files in `/usr/sbin/` to... 

1. Create a hidden file called `/.zramswap` in the root directory, with appropriate permissions and configuration for a swap file (works on btrfs!)
2. Preallocate the file to match the size of your zram disk
3. Set up a loopback device (`/dev/loop0`) connected to the file
4. Configure a ZRAM Swap drive in memory to use the loopback device as a backing device

I've also added a few of my own lines for configuration, including: 

- Using ZSTD compression
- Sending incompressible pages to the backing device instead of keeping them in RAM
- Enabling DISCARD on the swap device, which helps keep zram space smaller and more performant

