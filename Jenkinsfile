pipeline {
    agent any

    // Option 1: Polling (simple à configurer)
    triggers {
        pollSCM('H/5 * * * *')  // Toutes les 5 minutes
    }
    
    // Option 2: Webhook (meilleure performance)
    // triggers {}  // Laisser vide pour webhook pur

    options {
        // Empêcher les déclenchements simultanés du même job
        disableConcurrentBuilds()
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm  // Récupère automatiquement le code
            }
        }
        
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
                // Si vous avez des tests : bat 'npm test'
            }
        }

        stage('Build') {
            steps {
                echo 'Compilation de l\'application...'
                bat 'npm run build'
            }
        }

        stage('Déploiement') {
            when {
                branch 'main'  // Déployer seulement depuis main
            }
            steps {
                echo 'Déploiement en cours...'
                // Vos étapes de déploiement
            }
        }
    }

    post {
        success {
            echo 'Pipeline réussi ✓'
        }
        failure {
            echo 'Pipeline échoué ✗'
        }
    }
}
