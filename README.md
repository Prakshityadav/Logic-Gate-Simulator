# Logic-Gate-Simulator
import java.util.ArrayList;
import java.util.List;
import java.util.Scanner;

// Interface for logic gates
interface LogicGate {
    boolean getOutput();
}

// AND Gate implementation
class AndGate implements LogicGate {
    private boolean input1;
    private boolean input2;

    public AndGate(boolean input1, boolean input2) {
        this.input1 = input1;
        this.input2 = input2;
    }

    @Override
    public boolean getOutput() {
        return input1 && input2;
    }
}

// OR Gate implementation
class OrGate implements LogicGate {
    private boolean input1;
    private boolean input2;

    public OrGate(boolean input1, boolean input2) {
        this.input1 = input1;
        this.input2 = input2;
    }

    @Override
    public boolean getOutput() {
        return input1 || input2;
    }
}

// NOT Gate implementation
class NotGate implements LogicGate {
    private boolean input;

    public NotGate(boolean input) {
        this.input = input;
    }

    @Override
    public boolean getOutput() {
        return !input;
    }
}

// NAND Gate implementation
class NandGate implements LogicGate {
    private boolean input1;
    private boolean input2;

    public NandGate(boolean input1, boolean input2) {
        this.input1 = input1;
        this.input2 = input2;
    }

    @Override
    public boolean getOutput() {
        return !(input1 && input2);
    }
}

// NOR Gate implementation
class NorGate implements LogicGate {
    private boolean input1;
    private boolean input2;

    public NorGate(boolean input1, boolean input2) {
        this.input1 = input1;
        this.input2 = input2;
    }

    @Override
    public boolean getOutput() {
        return !(input1 || input2);
    }
}

// XOR Gate implementation
class XorGate implements LogicGate {
    private boolean input1;
    private boolean input2;

    public XorGate(boolean input1, boolean input2) {
        this.input1 = input1;
        this.input2 = input2;
    }

    @Override
    public boolean getOutput() {
        return input1 ^ input2; // XOR logic
    }
}

// XNOR Gate implementation
class XnorGate implements LogicGate {
    private boolean input1;
    private boolean input2;

    public XnorGate(boolean input1, boolean input2) {
        this.input1 = input1;
        this.input2 = input2;
    }

    @Override
    public boolean getOutput() {
        return !(input1 ^ input2); // XNOR logic
    }
}

// Circuit class to combine gates
class Circuit {
    private List<LogicGate> gates;

    public Circuit() {
        gates = new ArrayList<>();
    }

    public void addGate(LogicGate gate) {
        gates.add(gate);
    }

    public void simulate() {
        for (int i = 0; i < gates.size(); i++) {
            System.out.println("Gate " + (i + 1) + " Output: " + gates.get(i).getOutput());
        }
    }
}

// Half Adder implementation
class HalfAdder {
    private boolean inputA;
    private boolean inputB;

    public HalfAdder(boolean inputA, boolean inputB) {
        this.inputA = inputA;
        this.inputB = inputB;
    }

    public boolean getSum() {
        return inputA ^ inputB; // XOR for sum
    }

    public boolean getCarry() {
        return inputA && inputB; // AND for carry
    }
}

// Full Adder implementation
class FullAdder {
    private boolean inputA;
    private boolean inputB;
    private boolean carryIn;

    public FullAdder(boolean inputA, boolean inputB, boolean carryIn) {
        this.inputA = inputA;
        this.inputB = inputB;
        this.carryIn = carryIn;
    }

    public boolean getSum() {
        // (A XOR B) XOR CarryIn
        return (inputA ^ inputB) ^ carryIn;
    }

    public boolean getCarryOut() {
        // (A AND B) OR ((A XOR B) AND CarryIn)
        return (inputA && inputB) || ((inputA ^ inputB) && carryIn);
    }
}



public class Mainp {
    public static void main(String[] args) {
        // Create a circuit
        Circuit circuit = new Circuit();

        // Created gates with inputs
        LogicGate andGate = new AndGate(true, false);  // AND gate
        LogicGate orGate = new OrGate(true, false);    // OR gate
        LogicGate notGate = new NotGate(true);          // NOT gate
        LogicGate nandGate = new NandGate(true, false); // NAND gate
        LogicGate norGate = new NorGate(true, false);   // NOR gate
        LogicGate xorGate = new XorGate(true, false);   // XOR gate
        LogicGate xnorGate = new XnorGate(true, false);  // XNOR gate

        // Added gates to the circuit
        circuit.addGate(andGate);
        circuit.addGate(orGate);
        circuit.addGate(notGate);
        circuit.addGate(nandGate);
        circuit.addGate(norGate);
        circuit.addGate(xorGate);
        circuit.addGate(xnorGate);


        // Created and added a half adder
        HalfAdder halfAdder = new HalfAdder(true, false);
        System.out.println("Half Adder - Sum: " + halfAdder.getSum());
        System.out.println("Half Adder - Carry: " + halfAdder.getCarry());

        // Created and added a full adder
        FullAdder fullAdder = new FullAdder(true, true, false);
        System.out.println("Full Adder - Sum: " + fullAdder.getSum());
        System.out.println("Full Adder - Carry Out: " + fullAdder.getCarryOut());

        // Simulating the basic gates in the circuit
        circuit.simulate();
        
        // Below code is written to take user input//


//        Scanner scanner = new Scanner(System.in);
//        Circuit circuit = new Circuit();
//
//        // User input for AND gate
//        System.out.println("Enter first input for AND gate (true/false): ");
//        boolean andInput1 = scanner.nextBoolean();
//        System.out.println("Enter second input for AND gate (true/false): ");
//        boolean andInput2 = scanner.nextBoolean();
//        LogicGate andGate = new AndGate(andInput1, andInput2);
//        circuit.addGate(andGate);
//
//        //Repeat similar blocks for other gates (OR, NOT, NAND, NOR, XOR, XNOR)
//
//        // Taking User input for Half Adder
//        System.out.println("Enter first input for Half Adder (true/false): ");
//        boolean haInputA = scanner.nextBoolean();
//        System.out.println("Enter second input for Half Adder (true/false): ");
//        boolean haInputB = scanner.nextBoolean();
//        HalfAdder halfAdder = new HalfAdder(haInputA, haInputB);
//        System.out.println("Half Adder - Sum: " + halfAdder.getSum());
//        System.out.println("Half Adder - Carry: " + halfAdder.getCarry());
//
//        // Taking User input for Full Adder
//        System.out.println("Enter first input for Full Adder (true/false): ");
//        boolean faInputA = scanner.nextBoolean();
//        System.out.println("Enter second input for Full Adder (true/false): ");
//        boolean faInputB = scanner.nextBoolean();
//        System.out.println("Enter Carry In for Full Adder (true/false): ");
//        boolean carryIn = scanner.nextBoolean();
//        FullAdder fullAdder = new FullAdder(faInputA, faInputB, carryIn);
//        System.out.println("Full Adder - Sum: " + fullAdder.getSum());
//        System.out.println("Full Adder - Carry Out: " + fullAdder.getCarryOut());
//
//        // Simulating the basic gates in the circuit
//        circuit.simulate();
//
//        // Closing the scanner
//        scanner.close();
    }
}
