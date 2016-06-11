troykinsella.archive
====================

[![Build Status][travis-image]][travis-url]

An ansible role for fetching and unpacking archives, and verifying their checksums.

Role Variables
--------------

* archive_file_name: The archive file name.
* archive_file_mode: Optional. The file mode of the fetched archive. Default: 644.
* archive_url: The full url at which the archive can be downloaded.
* archive_fetch_headers: Optional. Headers to pass in the http archive fetch. Default: "". Format: "key:value,key:value".
* archive_checksum: The expected checksum of the fetched archive.
* archive_checksum_algorithm: Optional. The checksum algorithm: md5, sha1, sha256, for example - simply depends on the availability of the sum tool. Default: sha256.
* archive_cache_path: Optional. The directory path into which the archive will be downloaded. Default: /usr/local/pkg.
* archive_destination_path: Optional. The directory path into which the archive contents will be extracted. Default: /usr/local.
* archive_extracted_file_name: The expected name of the root file or directory that is extracted from the archive.
* archive_destination_file_name: Optional. Rename the extracted file to this value.

Example Playbook
----------------

    - hosts: servers
      roles:
        - role: troykinsella.archive
          archive_file_name: go1.5.3.linux-amd64.tar.gz
          archive_file_mode: 0700
          archive_url: https://storage.googleapis.com/golang/{{ archive_file_name }}
          archive_checksum: 43afe0c5017e502630b1aea4d44b8a7f059bf60d7f29dfd58db454d4e4e0ae53
          archive_checksum_algorithm: sha256
          archive_cache_path: /usr/local/pkg
          archive_destination_path: /usr/local/
          archive_extracted_file_name: go
          archive_destination_file_name: go1.5.3 # Move the extracted file/dir

Platforms
---------

(Untested)

* EL
* Fedora
* opensuse
* Amazon
* Ubuntu
* Debian

License
-------

MIT

[travis-image]: https://travis-ci.org/troykinsella/ansible-archive.svg?branch=master
[travis-url]: https://travis-ci.org/troykinsella/ansible-archive
