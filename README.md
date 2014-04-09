goqr
====

goqr - a [QRcode](http://en.wikipedia.org/wiki/QR_code) generator written in Go.

### Install

goqr is available at github.com. Get it by running.

    $ go get github.com/kiktomo/goqr

### Sample code

    package main
    
    import (
        "github.com/kiktomo/goqr"
        "image/png"
        "os"
    )
    
    func main() {
    
        // "0123456789" -> Numeric mode
        // "0123456789ABCDEFGHIJKLMNOPQRSTUVWXYZ $%*+-./:" -> Alphanumeric mode
        // "HELLO WORLD" -> Alphanumeric mode (upper-case only)
        // "Hello world" -> 8BitByte mode
        txt := "HELLO WORLD"
    
        // QRcode version:7
        // version := 0 (Auto)
        version := 7
    
        // QRcode error correction level: "M"
        // eclevel := 0 (Auto)
        eclevel := goqr.ECLevelM
    
        // Encode() returns image.Image
        qr, err := goqr.Encode(txt, version, eclevel)
        if err != nil {
            return
        }
    
        // png file output
        f, _ := os.Create("./qrcode.png")
        defer f.Close()
        png.Encode(f, qr)
    }

