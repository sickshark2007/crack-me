# + [#1 - Crack-Me GUI](https://github.com/sickshark2007/crack-me/tree/main/%231%20-%20Crack-Me%20GUI)
esse aqui dificultou um pouquinho mas não é nada que um cachorro adestrado consiga fazer

> [!IMPORTANT]
> Por o CrackMe ser em C# talvés você precise de uma ferramenta para você fazer debug, editar e recompilar, ou seja o [dnSpy](https://github.com/julianorinaldi/dnSpy#:~:text=Uma%20ferramenta%20para%20voc%C3%AA%20fazer,tenha%20o%20c%C3%B3digo%20fonte%20dispon%C3%ADvel.)

## 1. Descobrindo a desgraça dessa Senha
1. Assim como o outro tutorial, precisamos de um Descompilador, então providencie.
2. `Uma Dica`: Todo programa que tiver algo como "***_Load" ou "***_Click", é bem provavel que seja um programa em CSharp
3. Vi que o programa foi feito em CSharp pela descompilação do GHidra que por sua vez tinha funçôes como `button1_Click` e `Home_Load`
4. Agora que descobrimos que o Programa foi feito em CSharp temos que migrar para o nosso querido (desgraça que o diabo providenciou) o [dnSpy](https://github.com/julianorinaldi/dnSpy#:~:text=Uma%20ferramenta%20para%20voc%C3%AA%20fazer,tenha%20o%20c%C3%B3digo%20fonte%20dispon%C3%ADvel.)
5. Agora que provavelmente você levantou a bunda da sua cadeira e está no dnSpy, irei lhe amostrar um breve resumo de cada função extraida pelo dnSpy:
6. antes que você me lixe e me denuncie para a PF por roubar o coração da morena, Um aviso: Descartei partes que achei desnecessario para o tutorial (quase me joguei fora)
 ![Print](https://github.com/sickshark2007/crack-me/blob/main/%231%20-%20Crack-Me%20GUI/mapa_mental.png)
7. Quando o botão "Start Program Now" for clicado executará `Start_Click` quando tal função for executada, será verificado se o arquivo "validate.key" existe,
se ele não existir retornará em You cannot start this program. Missing License Key. (Tradução: Você não pode iniciar este programa. Chave de licença ausente.), Caso exista irá comparar a senha que está no arquivo `license.key` com a do `validate.key`.
8. Agora que você descobriu que a senha que está sendo comparada com uma senha dentro de um arquivo precisa descobrir de ondes caralhos está vindo está senha para ser inserida dentro do arquivo
e digamos que isso não é um problema até porque com o uso do ``Ctrl + F`` você acha facil facil as funções que fazem manuseio de tal arquivo
9. Logo no `Home_Load` (função que é executada quando a interface é carregada ou está prestes a carregar) você verá isto:
```c++
private void Home_Load(object sender, EventArgs e)
{
  if (!File.Exists("license.key"))
  {
    File.WriteAllText("license.key", Home.licensekey);
  }
}
```
9. Se você não é um zombie sem cabeça ou o Monark irá raciocinar em imediato que se o arquivo `license.key` não existir ele será criado
10. Ai está meus amigos (não tenho amigos) aonde temos uma brecha de onde caralhos pegar a senha (não seja burro, obviamente estou falando do `licensekey`)
11. Se tratando de Home.`licensekey` é uma variavel portando dando novamente uma pesquisa no codigo sobre a variavel, veremos o seguinte:
```C
// Token: 0x04000002 RID: 2
private static string licensekey = "AVB89-QQRT6-PO34R-0023H-KKL563";
```
12. ai está, a senha é `AVB89-QQRT6-PO34R-0023H-KKL563`

## 2. Descobrindo a senha através de pesquisa (só presta em apps pequenos)
esse metodo é inutil, basicamente só fiquei olhando em cada string que parecia meramente com um codigo de licença kkkkkkkkkkkkkkkkkk e por sinal achei ainda caçando que nem um doente

![a](https://github.com/sickshark2007/crack-me/blob/main/%231%20-%20Crack-Me%20GUI/pass.png)

#### Parabens garoto você conseguiu crackear um programinha =)
> Agora pegue todo seu dinheiro e me doe via pix, Scooby roubou meu dinheiro para comprar verdinha
