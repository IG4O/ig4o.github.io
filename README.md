import java.util.Scanner;

class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        //System.out.println("####################### PALCO #######################");

        int menu = 0, adm, lugareslivres , cliente, fila, assento, filaCancelar, assentoCancelar;
        boolean estudante;
        int ingressoEstudante = 0;
        float valorIngresso = 50.00f;
        float valortotal = 0;

        Teatro teatro = new Teatro(15, 10);

        while (true){ //Inserido  o while true para que fique em loop
            System.out.println("Digite o numero conforme o menu desejado:");
            System.out.println("1 > Area administrativa");
            System.out.println("2 > Area de clientes");
            System.out.println("3 > Sair");

            menu = scanner.nextInt();
            switch (menu){
                // Area administrativa
                case 1:
                    System.out.println("AREA ADMINISTRATIVA");
                    System.out.println("1 > Modificar o valor do ingresso");
                    System.out.println("2 > Visualizar mapa de assentos");
                    System.out.println("3 > valor total arrecadado com os ingressos");
                    adm = scanner.nextInt();
                    switch (adm){
                        case 1:
                            System.out.println("Digite o novo valor do ingresso: R$");
                            valorIngresso = scanner.nextFloat();
                            break;
                        case 2:
                            teatro.mostrarMapa();
                            break;
                        case 3:
                   
                            break;
                    }
                    break;
                // Area cliente
                case 2:
                    System.out.println("AREA DO CLIENTE");
                    System.out.println("1 > Visualizar mapa de assentos");
                    System.out.println("2 > Realizar reserva");
                    System.out.println("3 > Cancelar reserva");
                    cliente = scanner.nextInt();
                    switch (cliente){
                        case 1:
                            teatro.mostrarMapa();
                            break;
                        case 2:
                            System.out.println("Digite a fila e o assento. Ex: 0(fila) 1(assento)");
                            fila = scanner.nextInt();
                            assento = scanner.nextInt();
                            System.out.println("Estudante? (true/false)");
                            estudante = scanner.nextBoolean();
                            if(fila >= 0 && fila < 15 && assento >= 0 && assento < 10 ){
                                if (teatro.getAssentos()[fila][assento].getStatusAssento() == '_') {
                                    teatro.getAssentos()[fila][assento].reservar(estudante);
                                    if(estudante){
                                        ingressoEstudante++;
                                        valortotal = valorIngresso/2;
                                    } else {
                                        valortotal = valorIngresso; 
                                    }                                                                                                                                           
                                } else {
                                    System.out.println("Assento ocupado!");
                                }               
                            } else {
                                System.out.println("Assento invalido!");
                            }
                            break;
                        case 3:
                            System.out.println("Fila e assentto da reserva para cancelar");
                            filaCancelar = scanner.nextInt();
                            assentoCancelar = scanner.nextInt();
                            if (filaCancelar >= 0  && filaCancelar < 15 && assentoCancelar >= 0 && assentoCancelar < 10){
                                if(teatro.getAssentos()[filaCancelar][assentoCancelar].getStatusAssento() == 'R'){
                                    teatro.getAssentos()[filaCancelar][assentoCancelar].reservar(false);
                                    valortotal -= valorIngresso/2;
                                    ingressoEstudante--;
                                } else{
                                    System.out.println("Assento não está ocupado para ser cancelado. ");
                                }
                            } else{
                                System.out.println("Assento inválido.");
                            }
                            break;
                    }
                case 3:
                    System.out.println("Saindo do sistema");
                    System.exit(0);
                    break;                    
                default:
                    System.out.println("Invalido");                
            
            }     
                   
        }
        
    }
}

// Criei a classe teatro para que a parte da matriz focasse aqui.
class Teatro{
    public Assento[][] assento;

    public Teatro(int filas, int colunas) {
        int i, j;
        assento = new Assento[filas][colunas];
        for (i = 0; i < filas; i++) {
            for (j = 0; j < colunas; j++) {
                assento[i][j] = new Assento();
            }
        }
    }

    public void mostrarMapa() {
        int i, j;
        System.out.println("#########ESPETACULO#########");
        for (i = 0; i < assento.length; i++) {
            for (j = 0; j < assento[i].length; j++) {
                System.out.print(assento[i][j].getStatusAssento());
            }
            System.out.println();
        }
    }

    public Assento[][] getAssentos() {
        return assento;
    }
}

class Assento{
    public char status;

    public Assento(){
        status = '_';
    }

    public char getStatusAssento(){
        return status;
    }

    public void reservar(boolean estudante){
        if (status == '_'){
            if(estudante){
                System.out.println("Reserva de estudante confirmada!"); 
                               
            } else {
                System.out.println("Reserva confirmada");                
            } 
            status = 'R';
        } else {
            System.out.println("Assento indisponivel");
        }
    }

    public void cancelarReserva(){
        if (status == 'X'){
            System.out.println("Reserva cancelada");
            status = '_';            
        } else {
            System.out.println("Assento não está ocupado para ser cancelado.");
        }
    }

}

