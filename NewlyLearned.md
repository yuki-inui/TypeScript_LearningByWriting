# 新たな知見

## 型一覧
### string型  
  ```
  const name : string = ' ';
  const firstName: string = 'Michael';
  const lastName : string = 'Jackson';
  const fullName : string = '${firstName} ${lastName}';
  ```
  このようにテンプレートリテラルも``string``として扱うことができる。  

  ```
  const name : string = 'Michael Jackson' + 12334;
  ```
  このように ``文字列``+``数字``であれば``string型``になる。  

### number型
  ```
  const nan : number = 0 / 0;             //Nan はnumber
  const infinity : number = 1 / 0;        //Infinity はnumber
  const minusInfinity : number = -1 / 0;  //-Infinity は number
  ```
  `Nan`や`Infinity`や`-Infinity`はTypesriptでは`number型`として扱われる。  


### boolean型
  ```
  const id : string = '';
  const hasId1 : boolean = Boolean(id) //OK
  const hasId2 : boolean = !!id // OK
  ```
  ``boolean型``はtrueとfalseしか返さないが、変数などを代入したい場合は  
  ``Boolean()``や``!!``を使うなどする。  

### オブジェクト型
シンタックスルール  
```
//　（改行あり + セミコロンなし)
//   OK
const person1 : {
  name: string
  age: number
} = {
  name: 'Michael Jackson',
  age: 20,
}

//（改行あり + セミコロンあり)
// OK
const person2 : {
  name: string;
  age: number;
} = {
  name: 'Michael Jackson',
  age: 20,
}

// (改行なし + セミコロnなし)
// error
const person3: {name: string age: number} = {
  name: 'Mickael jackson',
  age: 20,
}

//(改行なし + セミコロnあり)
// OK
const person4: {name: string; age: number;} = {
  name : 'Michael Jackson',
  age: 30,
}

```

## 型推論
型推論における``let``と``const``の挙動違い。  
1. プリミティブなリテラル値を`const`で宣言された変数に代入する場合、その変数は代入された値のリテラル型と推論される。  
2. プリミティブなリテラル値を`let`で宣言されたヘンスに代入する場合、それは通常のデータ型として扱われる。 

### literal type widening
上記のように`const`と`let`では推論が違う。理由は

1. ``const``で宣言された変数は、値を再代入できない。例えば、``const name = 'Micael jackson'   
と宣言した場合、`name`変数は`Michael jackson`以外の値にならない。そのため``string型``ではなく``Mickael　jackson`として扱う。
2. ``let``は宣言した変数や、オブジェクトのバリューはさいだいにゅ出来てしまう。

これらの違いは、対象が「ミュータブル(可変)かいミュータブル(不変)か」である。  
これを念頭にすると、``const``は不変である。また``let``は可変である。  


