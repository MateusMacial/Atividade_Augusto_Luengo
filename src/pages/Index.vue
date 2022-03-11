<template>
  <q-page class="flex flex-center">
    <div class="q-ma-md">
      <div class="row-1">
        <div class="col">
          <h5>Informações do Aluno</h5>
          <h6>
            <p>Nome: Mateus Macial Ferreira</p>
            <p>Turma: 2020</p>
          </h6>
        </div>
      </div>
    
      <div class="row-2">
        <div class="col">
          <h5>Solução dos exercicios:</h5>
          <h6>1 - Escreva um programa que mostre a soma de todos os divisores de um dado número X. Um
          divisor é qualquer número menor que X cujo resto da divisão é igual a 0.</h6> 
          <textarea rows="13" cols="60" style="resize: none">
            testarPrimeiroExercicio () {
              const valorInicial = this.primeiroValor
              let divisores = []
              for (let i = valorInicial; i > 0; i--) {
                if (valorInicial % i === 0) {
                  divisores.push(i)
                }
              }
              this.resultadoPrimeiroExercicio = divisores
              this.$refs.resultadoPrimeiroExercicio.show()
              this.primeiroValor = 0
            }
          </textarea>
        </div>
        <q-btn class="q-ma-md" color="blue" text-color="black" label="Testar" @click="testarExercicio(1)" />
      </div>

      <div class="row-2">
        <div class="col">
          <h6>2 – Considere dois pontos no espaço 2D com as seguintes coordenadas: A(x 1 , y 1 ) e B(x 2 ,y 2 ).
            Escreva um programa que calcule tal distância para coordenadas de dois pontos informados
            pelo usuário.</h6> 
          <textarea rows="8" cols="90" style="resize: none">
            const primeiraConta = this.primeiroValor - this.segundoValor
            const segundaConta = this.terceiroValor - this.quartoValor;
            const terceiraConta = Math.sqrt(Math.pow(primeiraConta, 2) + Math.pow(segundaConta, 2));

            this.resultado = terceiraConta
            this.$refs.resultado.show()
          </textarea>
        </div>
        <q-btn class="q-ma-md" color="blue" text-color="black" label="Testar" @click="testarExercicio(2)" />
      </div>

      <div class="row-2">
        <div class="col">
          <h6>3 - Dada uma frase de entrada por um usuário, faça um programa que conte a ocorrência de
          cada palavra nesta frase. O programa não deve distinguir letras maiúsculas e minúsculas.</h6> 
          <textarea rows="18" cols="60" style="resize: none">
            testarTerceiroExercicio () {
              let frase = this.primeiroValor
              const palavras = frase.split(' ')
              let arrayFinal = []

              palavras.forEach(palavra => {
                let contador = 0
                for(let i = 0; i <= palavras.length; i++){
                  if(palavra === palavras[i]){
                    contador ++
                  }
                }
                arrayFinal.push(palavra + ' ocorre ' + contador + ' vez(es).')
              })
              this.resultadoExercicioTres = arrayFinal
              this.$refs.resultado.show()
            }
          </textarea>
        </div>
        <q-btn class="q-ma-md" color="blue" text-color="black" label="Testar" @click="testarExercicio(3)" />
      </div>

      <div class="row-2">
        <div class="col">
          <h6>4 – Faça um programa que leia uma string de números como entrada de um usuário que
          representa uma matriz e diga qual dimensão dela (quantidade de linhas e colunas). As linhas
          da matriz são separadas por um caractere de ponto e vírgula ‘;’e as colunas são separadas por
          um espaço vazio ‘ ’.</h6> 
          <textarea rows="13" cols="60" style="resize: none">
            const dimencaoUm = this.primeiroValor.split(';')
            const dimencaoDois = dimencaoUm[0].split(' ')
            this.resultado = 'Matriz de: ' + dimencaoUm.length + ' X ' +  dimencaoDois.length
            this.$refs.resultado.show()
          </textarea>
        </div>
        <q-btn class="q-ma-md" color="blue" text-color="black" label="Testar" @click="testarExercicio(4)" />
      </div>

      <div class="row-2">
        <div class="col">
          <h6>5 – Dado um número inteiro positivo N como entrada de um usuário, escreva um programa
          que mostre os primeiros N números da sequência de Fibonacci. (A sequência de Fibonacci é
          iniciada por 0 e 1, e o próximo número é sempre a soma dos dois últimos).</h6> 
          <textarea rows="10" cols="63" style="resize: none">
            console.log('quinto exercicio')
            const quantidadeValores = this.primeiroValor
            let arraySequencia = [0, 1]
            for(let i = 1; i < quantidadeValores - 1; i++){
              arraySequencia.push(arraySequencia[i] + (arraySequencia[i - 1]))
            }
            this.resultado = arraySequencia
            this.$refs.resultado.show()
          </textarea>
        </div>
        <q-btn class="q-ma-md" color="blue" text-color="black" label="Testar" @click="testarExercicio(5)" />
      </div>
    </div>

    <q-dialog ref="dialogValores" persistent>
      <q-card style="min-width: 350px">
        <q-card-section>
          <div class="text-h6">Digite um valor:</div>
        </q-card-section>

        <q-card-section class="q-pt-none">
          <q-input dense v-model="primeiroValor" autofocus label="Primeiro Valor" />
        </q-card-section>
        <q-card-section class="q-pt-none" v-if="this.exercicio === 2" >
          <q-input dense v-model="segundoValor" autofocus label="Segundo Valor" />
        </q-card-section>
        <q-card-section class="q-pt-none" v-if="this.exercicio === 2" >
          <q-input dense v-model="terceiroValor" autofocus label="Terceiro Valor" />
        </q-card-section>
        <q-card-section class="q-pt-none" v-if="this.exercicio === 2" >
          <q-input dense v-model="quartoValor" autofocus label="Quarto Valor" />
        </q-card-section>

        <q-card-actions align="right" class="text-primary">
          <q-btn flat label="Cancelar" v-close-popup />
          <q-btn flat label="Confirmar" v-close-popup @click="executar" />
        </q-card-actions>
      </q-card>
    </q-dialog>

    <q-dialog ref="resultado" @hide="limpar()">
      <q-card>
        <q-card-section>
          <div class="text-h6">Resultado</div>
        </q-card-section>
        <q-card-section class="q-pt-none" v-if="this.exercicio !== 3">
          {{ resultado }}
        </q-card-section>
        <q-card-section class="q-pt-none" v-if="this.exercicio === 3">
          <p v-for="frase in resultadoExercicioTres" :key="frase">
              {{ frase }}
          </p>
        </q-card-section>
        <q-card-actions align="right">
          <q-btn flat label="OK" color="primary" v-close-popup />
        </q-card-actions>
      </q-card>
    </q-dialog>
  </q-page>
</template>

<script>
export default {
  name: 'PageIndex',
  data() {
    return {
      primeiroValor: 0,
      segundoValor: 0,
      terceiroValor: 0,
      quartoValor: 0,
      resultado: '',
      resultadoExercicioTres: [],
      exercicio: 0
    }
  },
  methods: {
    executar () {
      switch (this.exercicio) {
        case 1:
          this.testarPrimeiroExercicio()
          break
        case 2: 
          this.testarSegundoExercicio()
          break
        case 3: 
          this.testarTerceiroExercicio()
          break
        case 4: 
          this.testarQuartoExercicio()
          break
        case 5: 
          this.testarQuintoExercicio()
          break
      }
    },
    testarExercicio (exercicio) {
      this.exercicio = exercicio
      this.$refs.dialogValores.show()
    },
    testarPrimeiroExercicio () {
      const valorInicial = this.primeiroValor
      let divisores = []
      for (let i = valorInicial; i > 0; i--) {
        if (valorInicial % i === 0) {
          divisores.push(i)
        }
      }
      this.resultado = divisores
      this.$refs.resultado.show()
    },
    testarSegundoExercicio () {
      const primeiraConta = this.primeiroValor - this.segundoValor
      const segundaConta = this.terceiroValor - this.quartoValor;
      const terceiraConta = Math.sqrt(Math.pow(primeiraConta, 2) + Math.pow(segundaConta, 2));

      this.resultado = terceiraConta
      this.$refs.resultado.show()
    },
    testarTerceiroExercicio () {
      let frase = this.primeiroValor
      const palavras = frase.split(' ')
      let arrayFinal = []

      palavras.forEach(palavra => {
        let contador = 0
        for(let i = 0; i <= palavras.length; i++){
          if(palavra === palavras[i]){
            contador ++
          }
        }
        arrayFinal.push(palavra + ' ocorre ' + contador + ' vez(es).')
      })
      this.resultadoExercicioTres = arrayFinal
      this.$refs.resultado.show()
    },
    testarQuartoExercicio () {
      const dimencaoUm = this.primeiroValor.split(';')
      const dimencaoDois = dimencaoUm[0].split(' ')
      this.resultado = 'Matriz de: ' + dimencaoUm.length + ' X ' +  dimencaoDois.length
      this.$refs.resultado.show()
    },
    testarQuintoExercicio () {
      console.log('quinto exercicio')
      const quantidadeValores = this.primeiroValor
      let arraySequencia = [0, 1]
      for(let i = 1; i < quantidadeValores - 1; i++){
        arraySequencia.push(arraySequencia[i] + (arraySequencia[i - 1]))
      }
      this.resultado = arraySequencia
      this.$refs.resultado.show()
    },
    limpar () {
      console.log('limpar')
      this.primeiroValor = 0
      this.segundoValor = 0
      this.terceiroValor = 0
      this.quartoValor = 0
    }
  }
}
</script>
