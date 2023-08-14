# [`donut.c`](https://www.a1k0n.net/2011/07/20/donut-math.html), but it's in `jq`

To run C donut:
Copy and paste below code in terminal: 

```sh
                  jq -nr 'def R(A;B;C
            ):range(A;B;C);def R(A):range
          (A);30as$s|1as$R1|2as$R2|7as$K2|(
        $s*$K2*3/(8*($R1+$R2)))as$K1|def t($A;$B
     ):($A|cos)as$cA|($B|cos)as$cB|($A|sin)as$sA|($B
    |sin)as$sB|R(0;2*3.1415;0.1)as$theta|($theta|cos
    )as$ct|($theta|sin)as$st|R(0;2*3.1415;0.05)as$phi|
   ($phi|cos)as$cp|($phi|sin)as$sp|($R2+$R1*$ct)as$cx|(
   $R1*$st)as$cy|{x:($cx*($cB*$cp+$sA*$sB*$sp)-$cy*$cA*
  $sB),y:($cx*($sB*$cp-$sA    *$cB*$sp)+$cy*$cA*$cB),z:(
 $K2+$cA*$cx*$sp+$cy             *$sA),ooz:(1/($K2+$cA*
$cx*$sp+$cy*$sA+0.01              )),L:($cp*$ct*$sB-$cA*
$ct*$sp-$sA*$st+$cB*              ($cA*$st-$ct*$sA*$sp))};
def r:def _d($dat;$pt             ):($s/2+$K1*$pt.ooz*
$pt.x|floor)as$xp|($s             /2-$K1*$pt.ooz*$pt
 .y|floor)as$yp|if($pt.L         <=0or $pt.ooz<=$dat
  .z[$yp][$xp])then$dat else{z:($dat.z|.[$yp][$xp]=
   $pt.ooz),o:($dat.o|.[$yp][$xp]=(".,-~:;=!*#$@"[
   $pt.L*8:$pt.L*8]))}end;reduce.[]as$p({o:[R($s)|
     [R($s)|" "]],z:[R($s)|[R($s)|0]]};_d(.;$p))|
         .o|.[]|join("");foreach repeat(0)as$_
           ({A:1,B:1};{A:(.A+0.07),B:(.B+
                 0.03)};[t(.A;.B)]|r)'
```

To run JavaScript donut:
Fork the git, open donutjs.js in VSCode or Terminal, install node, and type node donutjs.js