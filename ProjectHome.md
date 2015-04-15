<p align='right'>
<a href='http://goci.me/project/code.google.com/p/godec'><img width='76' align='absmiddle' height='18' src='https://goci.herokuapp.com/project/image/code.google.com/p/godec?.png' /></a>
<a href='http://godoc.org/code.google.com/p/godec/dec'><img width='94' align='absmiddle' height='18' alt='GoDoc' src='https://godoc.org/code.google.com/p/godec/dec?status.png' /></a>
</p>

**New development for this package is at https://speter.net/go/exp/math/dec/inf .**

API changes between the two packages:

<pre>
godec             inf.Dec              purpose<br>
---------------------------------------------------------------------------<br>
NewDecInt64(u)    NewDec(u,0)          favor common case for short API<br>
NewDec(u,s)       NewDecBig(u,s)       favor common case for short API<br>
(n/a)             z.SetUnscaled(u)     favor common case for short API<br>
z.SetUnscaled(u)  z.SetUnscaledBig(u)  favor common case for short API<br>
(n/a)             x.Unscaled()         consistency (NewDec*/SetUnscaled*)<br>
x.Unscaled()      x.UnscaledBig()      consistency (NewDec*/SetUnscaled*)<br>
z.Quo(x,y,s,r)    z.QuoRound(x,y,s,r)  consistency (combined operation)<br>
type Scaler       (unexported)         hide implementation details<br>
</pre>

Godec implements multi-precision decimal arithmetic for Go. The API and the implementation are based on and complement those in the multi-precision integer (Int) implementation in the Go library (math/big).

Installation:
```
go get code.google.com/p/godec/dec
```

See the [package docs](http://godoc.org/code.google.com/p/godec/dec) for details.

Limitations:
  * Support for formatting options is currently missing.
  * There is no support for potentially lossy conversions (e.g. float64 to Dec, Dec to int64, or Dec to float64) as the requirements for these usually differ depending on the use case.