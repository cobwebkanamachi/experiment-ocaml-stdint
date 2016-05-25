# experiment-ocaml-stdint
I wrote this for experiment on ocaml-stdint shown bellow.
https://github.com/andrenth/ocaml-stdint

test sequence:
download zip
unzip zip
cd extracteddir
oasis setup
make configure
make
vi main.ml

<pre>
#directory "./_build/lib";;
#load "./_build/lib/stdint.cma";;
(*
 * https://github.com/andrenth/ocaml-stdint/
 * http://stdint.forge.ocamlcore.org/doc/Stdint.Uint64.html
 * www.ueda.info.waseda.ac.jp/~sakai/ocaml/ocaml_intro1.txt
 *)
open Stdint

let _ =
  let a = Uint32.of_int 0x00000000ffffffff in 
  print_string ("org hex in  Uint32.of_int:");
  print_endline (Uint32.to_string_hex a);
  let a = Uint64.of_int 0x00000000ffffffff in 
  print_string ("org hex in  Uint64.of_int:");
  print_endline (Uint64.to_string_hex a);
  let b = Uint64.to_uint64 a in 
  print_string ("test: int 0x00000000ffffffff -> to_uint64:");
  print_endline (Uint64.to_string_hex b);
  let b = Uint64.to_uint16 a in 
  print_string ("test: int 0x00000000ffffffff -> uint16:");
  print_endline (Uint16.to_string_hex b);
  let a = Uint64.of_int 0x00000000ffffffff in 
  print_string ("test: int 0x00000000ffffffff -> of_int:");
  print_endline (Uint64.to_string_hex a);
  let a = Uint64.of_int 0x000000ffffffffff in 
  print_string ("test: int 0x000000ffffffffff -> of_int:");
  print_endline (Uint64.to_string_hex a);
  let a = Uint64.of_int 0x0000ffffffffffff in 
  print_string ("test: int 0x0000ffffffffffff -> of_int:");
  print_endline (Uint64.to_string_hex a);
  let a = Uint64.of_int 0x00ffffffffffffff in 
  print_string ("test: int 0x00ffffffffffffff -> of_int:");
  print_endline (Uint64.to_string_hex a);
  let a = Uint64.of_int 0x0fffffffffffffff in 
  print_string ("test: int 0x0fffffffffffffff -> of_int:");
  print_endline (Uint64.to_string_hex a);
(*
 *
 *)
  let a = Uint64.of_int 0x00000000ffffffff in 
  let b = Uint64.to_uint64 a in 
  print_string ("test: int 0x00000000ffffffff -> Unt64:");
  print_endline (Uint64.to_string_hex b);
  print_string ("test: int 0x00000000ffffffff -> of_int:");
  print_endline (Uint64.to_string_hex a);
(*
 * 
 *)
  let a = Uint64.of_int 0xffff in
  print_string ("test: int 0xffff-> Unt64:");
  print_endline (Uint64.to_string_hex a);
  let a = Uint64.of_int 0xffffffff in
  print_string ("test: int 0xffffffff-> Unt64:");
  print_endline (Uint64.to_string_hex a);
(*
 *
 *)
  print_endline (Uint64.to_string a);
  let b = Uint64.shift_left a  2 in
  print_endline (Uint64.to_string b);
  print_endline (Uint64.to_string_hex b);
  let c = Uint64.shift_left a  4 in
  print_endline (Uint64.to_string c);
  print_endline (Uint64.to_string_hex c);
  let d = Uint64.shift_left a  8 in
  print_endline (Uint64.to_string d);
  print_endline (Uint64.to_string_hex d);
  let e = Uint64.shift_left a  16 in
  print_endline (Uint64.to_string e);
  print_endline (Uint64.to_string_hex e);
  let f = Uint64.shift_left a  32 in
  print_endline (Uint64.to_string f);
  print_endline (Uint64.to_string_hex f);
  let g = Uint64.shift_left a  64 in
  print_endline (Uint64.to_string_hex g);


</pre>
then type bellow:
ocaml test.ml
<pre>
$ ocaml main.ml
org hex in  Uint32.of_int:0xffffffff
org hex in  Uint64.of_int:0xffffffffffffffff
test: int 0x00000000ffffffff -> to_uint64:0xffffffffffffffff
test: int 0x00000000ffffffff -> uint16:0xffff
test: int 0x00000000ffffffff -> of_int:0xffffffffffffffff
test: int 0x000000ffffffffff -> of_int:0xffffffffffffffff
test: int 0x0000ffffffffffff -> of_int:0xffffffffffffffff
test: int 0x00ffffffffffffff -> of_int:0xffffffffffffffff
test: int 0x0fffffffffffffff -> of_int:0xffffffffffffffff
test: int 0x00000000ffffffff -> Unt64:0xffffffffffffffff
test: int 0x00000000ffffffff -> of_int:0xffffffffffffffff
test: int 0xffff-> Unt64:0xffff
test: int 0xffffffff-> Unt64:0xffffffffffffffff
18446744073709551615
18446744073709551612
0xfffffffffffffffc
18446744073709551600
0xfffffffffffffff0
18446744073709551360
0xffffffffffffff00
18446744073709486080
0xffffffffffff0000
18446744069414584320
0xffffffff00000000
0xffffffffffffffff

</pre>
this is all.
