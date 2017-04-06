mahonia
=======

 character-set conversion library implemented in Go.

 Mahonia is a character-set conversion library implemented in Go.
 All data is compiled into the executable; it doesn't need any external data files.

 Copy from http://code.google.com/p/mahonia/

install
-------

  go get github.com/anlgo/mahonia

example
-------

```go
  package main
  import "fmt"
  import "github.com/anlgo/mahonia"
  func main(){
    enc := mahonia.NewEncoder("gbk")
	//converts a  string from UTF-8 to gbk encoding.

    gbkByte := enc.ConvertString("hello,世界")

    fmt.Println(gbkByte)
    fmt.Println(len(gbkByte))

    var dec mahonia.Decoder

    testBytes := []byte{0xC4, 0xE3, 0xBA, 0xC3, 0xA3, 0xAC, 0xCA, 0xC0, 0xBD, 0xE7, 0xA3, 0xA1}
    var testStr string
    testStr = string(testBytes)
    dec = mahonia.NewDecoder("gbk")

    if ret, ok := dec.ConvertStringOK(testStr); ok {
      fmt.Println("GBK to UTF-8: ", ret, " bytes:", testBytes)
    }
  }
```
