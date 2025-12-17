pipeline {
    agent any // Utilise n'importe quel exécuteur disponible

    stages {
        stage('Installation') {
            steps {
                echo 'Installation des dépendances...'
                bat 'npm install'
            }
        }

        stage('Linter & Tests') {
            steps {
                echo 'Vérification du code...'
                bat 'npm run lint'
                // On peut ajouter "npm test" si vous avez des tests
            }
        }

        stage('Build') {
            steps {
                echo 'Compilation de l\'application...'
                bat 'npm run build'
            }
        }

        stage('Déploiement (Simulation)') {
            steps {
                echo 'L\'application est prête à être déployée !'
                // Ici, on pourrait copier les fichiers vers un serveur
            }
        }
    }

    post {
        success {
            echo 'Félicitations ! Le pipeline a réussi.'
        }
        failure {
            echo 'Le pipeline a échoué. Vérifiez les logs.'
        }
    }
}