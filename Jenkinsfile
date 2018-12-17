node {
    stage ('checkout') {
        checkout scm
    }
    stage ('build') {
        // Copies the artifacts of plugin-a/master (plugin-a.txt) in to this workspace.
        copyArtifacts projectName: 'gateconsumes-pipeline/master'

        // Notify DevOptics that this run consumed plugin-a.txt.
        gateConsumesArtifact file: 'plugin-a.txt'

        // Creates a file called plugin-b.txt.
        sh "git rev-parse HEAD > plugin-b.txt"

        // Records plugin-b.txt as a produced artifact.
        archiveArtifacts artifacts: 'plugin-b.txt'
    }
    stage ('produce') {
        // Notify DevOptics that this run produced plugin-b.txt.
        gateProducesArtifact file: 'plugin-b.txt'
    }
}
