import java.util.ArrayList;
import java.util.List;

class Sala {
    private double tamanhoEmM2;

    public Sala(double tamanhoEmM2) {
        this.tamanhoEmM2 = tamanhoEmM2;
    }

    public double getTamanhoEmM2() {
        return tamanhoEmM2;
    }
}

class Andar {
    private List<Sala> salas;
    private double valorPorM2;

    public Andar(double valorPorM2) {
        this.valorPorM2 = valorPorM2;
        this.salas = new ArrayList<>();
    }

    public void adicionarSala(Sala sala) {
        salas.add(sala);
    }

    public double calcularAluguelDoAndar() {
        double total = 0;
        for (Sala sala : salas) {
            total += sala.getTamanhoEmM2() * valorPorM2;
        }
        return total;
    }
}

class Predio {
    private List<Andar> andares;

    public Predio() {
        this.andares = new ArrayList<>();
    }

    public void adicionarAndar(Andar andar) {
        andares.add(andar);
    }

    public double calcularAluguelTotal() {
        double total = 0;
        for (Andar andar : andares) {
            total += andar.calcularAluguelDoAndar();
        }
        return total;
    }
}

public class AluguelPredio {
    public static void main(String[] args) {
        // Criar o prédio
        Predio predio = new Predio();

        // Andar 1: valor R$ 30/m², 2 salas
        Andar andar1 = new Andar(30);
        andar1.adicionarSala(new Sala(50)); // sala de 50m²
        andar1.adicionarSala(new Sala(40)); // sala de 40m²

        // Andar 2: valor R$ 45/m², 3 salas
        Andar andar2 = new Andar(45);
        andar2.adicionarSala(new Sala(30)); // sala de 30m²
        andar2.adicionarSala(new Sala(35)); // sala de 35m²
        andar2.adicionarSala(new Sala(25)); // sala de 25m²

        // Adiciona andares ao prédio
        predio.adicionarAndar(andar1);
        predio.adicionarAndar(andar2);

        // Calcula e exibe o valor total de aluguel
        double totalAluguel = predio.calcularAluguelTotal();
        System.out.printf("Aluguel total do prédio: R$ %.2f%n", totalAluguel);
    }
}


