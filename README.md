# officecrypto-tool


officeCrypto is a library for js that can be used to decrypt and encrypt office(excel/ppt/word) files..

## Special Notes
The implementation of this library refers to [xlsx](https://www.npmjs.com/package/xlsx) and [xlsx-populate](https://www.npmjs.com/package/xlsx-populate), especially `xlsx-populate`, part of the source code reference and directly copied over.

Now it supports encryption and decryption of` MS office and WPS xlsx suffix files`, `xls suffix` encryption and decryption is not supported yet.

## Contents

- [officecrypto-tool](#officecrypto-tool)
  - [Special Notes](#special-notes)
  - [Contents](#contents)
  - [Install](#install)
  - [Examples](#examples)
  - [Supported encryption methods](#supported-encryption-methods)
    - [OFFICECRYPTO specs](#officecrypto-specs)
    - [Other](#other)
  - [Tests](#tests)
  - [Todo](#todo)
  - [Resources](#resources)
    - [In other languages](#in-other-languages)


## Install

```
npm/yarn/pnpm install officeCrypto
```

## Examples

```
const officeCrypto = require('officeCrypto');
const fs = require('fs').promises;

//decrypt a file with a password
(async ()=>{
        const input = await fs.readFile(`pass_test.xlsx`);
        const output = await officeCrypto.decrypt(input, {password: '123456'});
        await fs.writeFile(`out_success.xlsx`, output);
})()

//Setting up encrypted files with passwords
(async ()=>{
        const input = await fs.readFile(`test.xlsx`);
        const output = officeCrypto.encrypt(input, {password: '123456'});
        await fs.writeFile(`standard_out_success.xlsx`, output);
})()
```

## Supported encryption methods

### OFFICECRYPTO specs

* [x] ECMA-376 (Agile Encryption/Standard Encryption)
  * [x] MS-DOCX (OOXML) (Word 2007-2016)
  * [x] MS-XLSX (OOXML) (Excel 2007-2016)
  * [x] MS-PPTX (OOXML) (PowerPoint 2007-2016)
* [] Office Binary Document RC4 CryptoAPI
  * [] MS-DOC (Word 2002, 2003, 2004)
  * [] MS-XLS (Excel 2002, 2003, 2004) (experimental)
  * [] MS-PPT (PowerPoint 2002, 2003, 2004) (partial, experimental)
* [] Office Binary Document RC4
  * [] MS-DOC (Word 97, 98, 2000)
  * [] MS-XLS (Excel 97, 98, 2000) (experimental)
* [ ] ECMA-376 (Extensible Encryption)
* [ ] XOR Obfuscation

### Other

* [ ] Word 95 Encryption (Word 95 and prior)
* [ ] Excel 95 Encryption (Excel 95 and prior)
* [ ] PowerPoint 95 Encryption (PowerPoint 95 and prior)

PRs are welcome!

## Tests

With Jest:

```
pnpm i 
pnpm run test
```

## Todo

* [x] Add tests
* [x] Support decryption and encryption  with passwords
* [x] Support older encryption schemes
* [x] Add decryption tests for various file formats
* [ ] Support more encryption and decrytion 
* [ ] Support frontend

## Resources


* Technical Documents <https://learn.microsoft.com/en-us/openspecs/office_file_formats/MS-OFFFFLP/6ae2fd93-51fc-4e75-a54a-1b175c627b51>




### In other languages

* <https://github.com/opendocument-app/OpenDocument.core/blob/233663b039/src/internal/ooxml/ooxml_crypto.h>
* <https://github.com/qax-os/excelize>
* <https://github.com/nolze/msoffcrypto-tool>

