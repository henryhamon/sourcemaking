# Introdução de Método Estrangeiro
## Problema
Uma classe de utilidades não contém o método que você precisa e você não pode adicionar o método a aquela classe.
```
class Report {
  //...
  void sendReport() {
    $previousDate = clone $this->previousDate;
    $paymentDate = $previousDate->modify('+7 days');
    //...
  }
}
```

## Solução
Adicionar o método na classe cliente e passar um objeto da classe utilitária como um argumento.
```
class Report {
  //...
  void sendReport() {
    $paymentDate = $this->nextWeek($this->previousDate);
    //...
  }
  /**
   * Foreign method. Should be in Date.
   */
  private static function nextWeek(DateTime $arg) {
    $previousDate = clone $arg;
    return $previousDate->modify('+7 days');
  }
}
```

## Porque Refatorar
Você tem um código que usa os dados é métodos de uma certa classe. Você imagina que o código irá parecer e trabalhar muito melhor dentro de um método na classe. Mas você não pode adicionar o método a esta classe porque, por exemplo, a classe fica localizada em bibliotecas de terceiros.
Este refatoramento tem um custo muito grande quando o código que você quer mover para o método se repete muitas vezes em diferentes locais do seu programa.
Desde que você passa um objeto da classe utilitária aos parâmetros do novo método, você tem acesso a todos os campos dele. Dentro do método, você pode fazer praticamente tudo que você quiser, como se o método fizesse parte da classe utilitária.

## Benefícios
* Remove a duplicação de código. Se o seu código se repete em muitos lugares você pode substituir estes fragmentos de código com uma chamada de método. Isto é melhor do que duplicação, mesmo considerando que o método não está localizado em um local "ideal".

## Inconvenientes
* As razões para se manter um método de uma classe utilitária na classe cliente nem sempre vão ser claras para pessoas que irão dar manutenção ao código depois de você. Se o método pode ser usado em outras classes, você pode se beneficiar criando um encapsulamento para a classe utilitária e colocando o método ali. Isto também pode ser benéfico quando existem muitos destes métodos de utilidades. [Introdução de Extensão Local](https://github.com/henryhamon/sourcemaking/blob/master/3_refactoring/2_refactoring_techniques/2_moving_features_between_objects/8_introduce_local_extension.md) pode ajudar com isto.

## Como Refatorar
1. Crie um método na classe destinatária.
2. Neste método, crie um parâmetro para qual o objeto da classe utilitária será passado. Se este objeto pode ser obtido da classe cliente, você não precisa criar este parâmetro. 
3. Faça a extração dos fragmentos de código relevantes para este método e os substitua com a chamada de métodos.
4. Tenha certeza de deixar nos comentários a _tag_ Método Estrangeiro (_Foreign Method_), juntamente com o conselho de colocar este método em uma classe utilitária se isto se tornar possível mais tarde. Isto irá facilitar o entendimento do porque este método está localizado nesta classe particular para aqueles que irão manter o _software_ no futuro.