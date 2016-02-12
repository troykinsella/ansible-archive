troykinsella.fetch-archive
==========================

An ansible role for fetching and unpacking archives, and verifying their checksums.

Role Variables
--------------

* archive_file_name: "the archive file name"
* archive_url: "the full url at which the archive can be downloaded"
* archive_checksum: "the expected checksum of the fetched archive"
* archive_checksum_type: "the checksum algorithm: md5, sha1, sha256, for example - simply depends on the availability of the sum tool"
* archive_destination_path: "the directory path into which the archive will be downloaded and extracted"
* archive_extracted_dir_name: "the expected name of the root directory that is extracted from the archive"

Example Playbook
----------------

    - hosts: servers
      roles:
         - role: troykinsella.archive
           archive_file_name: go1.5.3.linux-amd64.tar.gz
           archive_url: https://storage.googleapis.com/golang/{{ archive_file_name }}
           archive_checksum: 43afe0c5017e502630b1aea4d44b8a7f059bf60d7f29dfd58db454d4e4e0ae53
           archive_checksum_type: sha256
           archive_destination_path: /usr/local/
           archive_extracted_dir_name: go

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
