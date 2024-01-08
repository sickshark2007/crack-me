# + [#0 - IOLI-Crackme](https://github.com/sickshark2007/crack-me/tree/main/%230%20-%20IOLI-Crackme)
tão facil que quase me matei escrevendo esse texto que obviamente ninguem vai ler

## 1. Metodo de Descobrir a Maldita Senha

> [!TIP]
> Uma Dica, Use este Metodo.

1. Basicamente é só colocar o [crackme.exe](https://github.com/sickshark2007/crack-me/blob/main/%230%20-%20IOLI-Crackme/crackme.exe) em um Descompilador, Tanto faz qual seja o importante é descompilar.
2. Depois de enfiar o aplicativo no descompilador igual a vida te fode todo dia, Descompila a função "main"
3. Depois de descompilar a função "main", É bem provavel que você veja algo ao menos semelhante a isto:
```c++
int __cdecl _main(int _Argc,char **_Argv,char **_Env)

{
  int iVar1;
  size_t in_stack_ffffffc0;
  char local_1c [24];
  
  __alloca(in_stack_ffffffc0);
  ___main();
  _printf("IOLI Crackme Level 0x00\n");
  _printf("Password: ");
  _scanf("%s",local_1c);
  iVar1 = _strcmp(local_1c,"250382");
  if (iVar1 == 0) {
    _printf("Password OK :)\n");
  }
  else {
    _printf("Invalid Password!\n");
  }
  return 0;
}
```

4. Depois que você se deparar com esse codigo mediocre parecendo o Presidente Lula de calcinha, você fica com uma cara de desgosto da vida (evento canonico de todo hackerman)
5. Se você não for um programador fajuto igual a mim, irá perceber que a verificação de senha é baseada no [strcmp](https://wagnergaspar.com/como-comparar-duas-strings-com-a-funcao-strcmp-na-linguagem-de-programacao-c/) que por sinal o resultado desta verificação está sendo armazenada na variavel "iVar1". E segundo a propia documentação da Linguagem C, O strcmp retorna a '0' quando as strings são identicas.
6. Ou seja a senha é `250382`

## 2. Metodo de Descobrir essa Porra
1. Mete a porra do aplicativo em um editor de Hexadecimal (realmente não me importa qual)
2. Procura a string `password` e depois de ter encontrado você vai se deparar com essa porra ai ó
![Ednaldo Pereira de Cueca](https://github.com/sickshark2007/crack-me/blob/main/%230%20-%20IOLI-Crackme/hexadecimal.png)
3. E a senha é `250382`, Vale ressaltar que este metodo é mais facil ter a parte 2 do ataque as torre gemeas do que mesmo você encontrar essa maldita senha
  
#### Parabens garoto você conseguiu crackear um programinha =)
> Agora pegue todo seu dinheiro e me doe via pix, estou passando fome e sendo forçado a programar para o [Daniel Fraga](https://portaldobitcoin.uol.com.br/pioneiro-do-bitcoin-daniel-fraga-da-sinal-de-vida-no-youtube/)
