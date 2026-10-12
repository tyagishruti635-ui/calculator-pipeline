ø
≈pipeline {
    agent any

    parameters {
        string(name: 'NUMBER1', defaultValue: '10', description: 'Enter first number')
        string(name: 'NUMBER2', defaultValue: '5', description: 'Enter second number')
        choice(name: 'OPERATION', choices: ['add', 'subtract', 'multiply', 'divide'], description: 'Select operation')
    }

    stages {
        stage('Calculate') {
            steps {
                script {
                    def a = params.NUMBER1.toDouble()
                    def b = params.NUMBER2.toDouble()
                    def op = params.OPERATION
                    def result

                    if (op == 'add') {
                        result = a + b
                    } else if (op == 'subtract') {
                        result = a - b
                    } else if (op == 'multiply') {
                        result = a * b
                    } else if (op == 'divide') {
                        if (b == 0) {
                            error('Cannot divide by zero')
                        }
                        result = a / b
                    }

                    echo "Result: ${result}"

                    mail(
                        to: "tyagishruti635@gmail.com",
                        subject: "Calculator Result",
                        body: "Number 1: ${a}\nNumber 2: ${b}\nOperation: ${op}\nResult: ${result}"
                    )
                }
            }
        }
    }
}
