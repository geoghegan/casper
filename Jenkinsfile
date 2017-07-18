node("docker") {
    docker.withRegistry('geoghegan/casper', 'dockerhub') {
    
        git url: "https://github.com/geoghegan/casper", credentialsId: 'github'
    
        sh "git rev-parse HEAD > .git/commit-id"
        def commit_id = readFile('.git/commit-id').trim()
        println commit_id
    
        stage "build"
        def app = docker.build "casper"
    
        stage "publish"
        app.push 'master'
        app.push "${commit_id}"
    }
}
