Introduction
============

This container will detect duplicate IP addresses on your network. This is done
using the arp-scan tool, and minimally parsing the output. The exit code is set
appropriately, so that you can use this with a cron job to scan your network
periodically.

To run:

    docker run --rm --net=host irasnyd/arpscan

Example Output
==============

No duplicates found:

    $ docker run --rm --net=host arpscan
    Looking for duplicate IP addresses using arp-scan ...
    No duplicates found! You have a healthy network!

Duplicates found:

    $ docker run --rm --net=host arpscan
    Looking for duplicate IP addresses using arp-scan ...
    10.1.2.3        00:11:22:33:44:55       Example Vendor A
    10.1.2.3        00:11:22:33:44:56       Example Vendor B (DUP: 1)
    10.1.2.3        00:11:22:33:44:57       Example Vendor C (DUP: 2)

    You have duplicates IP addresses on your network :-(
