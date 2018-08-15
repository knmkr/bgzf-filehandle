# bgzf-filehandle

[![NPM version](https://img.shields.io/npm/v/@gmod/bgzf-filehandle.svg?style=flat-square)](https://npmjs.org/package/@gmod/bgzf-filehandle)
[![Build Status](https://img.shields.io/travis/GMOD/bgzf-filehandle/master.svg?style=flat-square)](https://travis-ci.org/GMOD/bgzf-filehandle) 

Read indexed block-gzipped (BGZF) files, such as those created by bgzip, using uncompressed file offsets 

## Install

    $ npm install --save @gmod/bgzf-filehandle

## Usage

```js
const { BgzfFilehandle } = require('@gmod/bgzf-filehandle')

const f = new BgzfFilehandle({path: 'path/to/my_file.gz'})
// assumes a .gzi index exists at path/to/my_file.gz.gzi. can also
// pass `gziPath` to set it explicitly. Can also pass filehandles
// for the files: `filehandle` and `gziFilehandle`

// supports a subset of the NodeJS v10 filehandle API. currently
// just read() and stat()
const myBuf = Buffer.alloc(300)
await f.read(myBuf,0,300,23234)
// now use the data in the buffer

const { size } = f.stat() // stat gives the size as if the file were uncompressed
```

## Academic Use

This package was written with funding from the [NHGRI](http://genome.gov) as part of the [JBrowse](http://jbrowse.org) project. If you use it in an academic project that you publish, please cite the most recent JBrowse paper, which will be linked from [jbrowse.org](http://jbrowse.org).

## License

MIT © [Robert Buels](https://github.com/rbuels)
