pipeline {
    agent any // Utilise un agent disponible pour exécuter ce pipeline

    stages {
        stage('Clone Repository') {
            steps {
                // Cloner le dépôt à partir de GitHub
                git url: 'https://github.com/sserigne/gema-workspace.git', branch: 'main', credentialsId: 'github-credentials'
            }
        }

        stage('Install Dependencies') {
            steps {
                // Installer les dépendances, exemple pour un projet Node.js ou Java
                sh 'npm install' // Exemple pour Node.js, ajustez selon votre projet (ex: `mvn install` pour Maven)
            }
        }

        stage('Run Tests') {
            steps {
                // Exécuter les tests
                sh 'npm test' // Exemple pour Node.js, ajustez selon votre projet
            }
        }

        stage('Archive Results') {
            steps {
                // Archiver les résultats des tests, par exemple les fichiers de couverture ou de rapport
                archiveArtifacts '**/target/*.jar'  // Exemple pour Java, ajustez selon votre projet
                junit '**/target/test-*.xml' // Exemple pour publier les résultats des tests JUnit
            }
        }

        stage('Deploy') {
            steps {
                // Déployer l'application si nécessaire
                echo 'Déploiement en production'
                // Vous pouvez ajouter votre commande de déploiement ici
            }
        }
    }

    post {
        // Actions post-pipeline, comme notifier si le build a échoué ou réussi
        success {
            echo 'Le pipeline a réussi!'
        }
        failure {
            echo 'Le pipeline a échoué.'
        }
    }
}
