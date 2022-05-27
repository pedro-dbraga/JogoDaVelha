using System;

namespace jogo_da_velha
{
   class JogoDaVelha
    {
        private bool fimDeJogo;
        private char[] posicoes;
        private char vez;
        private int cont;

        public JogoDaVelha()
    {
        fimDeJogo = false;
        posicoes = new[] { '1', '2', '3', '4', '5', '6', '7', '8', '9' };
        vez = 'X';
        cont=0;
    }
    public void Iniciar()
    {
        while (!fimDeJogo)
        {
            RenderizarTabela();
            LerEscolhaDoUsuario();
            RenderizarTabela();
            VerificarFimDoJogo();
            MudarAVez();
        }
    }

    void MudarAVez()
    {
            vez = vez == 'X' ? 'O' : 'X';
    }

    void VerificarFimDoJogo()
    {
            if (cont < 5)
                return;

            if (ExisteVitoriaDiagonal() || ExisteVitoriaHorizontal() || ExisteVitoriaVertical())
            {
                fimDeJogo = true;
                Console.WriteLine($"Fim de jogo! Vitoria de {vez}.");
                return;
            }

            if (cont == 9)
            {
                fimDeJogo = true;
                Console.WriteLine("Empate");             
            }
    }


    private bool ExisteVitoriaHorizontal()
    {
            bool linha1 = posicoes[0] == posicoes[1] && posicoes[0] == posicoes[2];
            bool linha2 = posicoes[3] == posicoes[4] && posicoes[3] == posicoes[5];
            bool linha3 = posicoes[6] == posicoes[7] && posicoes[6] == posicoes[8];


            return linha1 || linha2 || linha3;
    }

    private bool ExisteVitoriaVertical()
    {
            bool coluna1 = posicoes[0] == posicoes[3] && posicoes[0] == posicoes[6];
            bool coluna2 = posicoes[1] == posicoes[4] && posicoes[1] == posicoes[7];
            bool coluna3 = posicoes[2] == posicoes[5] && posicoes[2] == posicoes[8];

            return coluna1 || coluna2 || coluna3;
        }

   private bool ExisteVitoriaDiagonal()
   {
            bool diagonal1 = posicoes[0] == posicoes[4] && posicoes[0] == posicoes[8];
            bool diagonal2 = posicoes[2] == posicoes[4] && posicoes[2] == posicoes[6];

            return diagonal1 || diagonal2;
        }
        void LerEscolhaDoUsuario()
    {
            Console.WriteLine("Agora é a vez de {0}", vez);
            bool conversao = int.TryParse(Console.ReadLine(), out int posicaoEscolhida);

            while (!conversao || !ValidarEscolhaUsuario(posicaoEscolhida))
            {
                Console.WriteLine("O campo escolhido é invalido.");
                Console.WriteLine("Escolha outro: ");
                conversao = int.TryParse(Console.ReadLine(), out posicaoEscolhida);
            }
            PreencherEscolha(posicaoEscolhida);
    }

        private void PreencherEscolha(int posicaoEscolhida)
        {
            int indice = posicaoEscolhida - 1;

            posicoes[indice] = vez;
            cont++;
        }

        private bool ValidarEscolhaUsuario(int posicaoEscolhida)
        {
            int indice = posicaoEscolhida - 1;

            return posicoes[indice] != 'O' && posicoes[indice] != 'X';

        }

    void RenderizarTabela()
    {
            Console.Clear();
            Console.WriteLine(ObterTabela());
    }
    private string ObterTabela()
    {
            return $"  {posicoes[0]}  |  {posicoes[1]}  |  {posicoes[2]}  \n" +
                   $"  {posicoes[3]}  |  {posicoes[4]}  |  {posicoes[5]}  \n" +
                   $"  {posicoes[6]}  |  {posicoes[7]}  |  {posicoes[8]}  \n\n";
        }
}
}
