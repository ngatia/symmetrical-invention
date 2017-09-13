node("master") {
    docker.withRegistry('https://hub.docker.com/u/ngatia/', 'dockerhub') {

        git url: "https://github.com/ngatia/symmetrical-invention", credentialsId: 'b99df07a-54e2-446a-bd3f-2355d5c9fb15'

        sh "git rev-parse HEAD > .git/commit-id"
        def commit_id = readFile('.git/commit-id').trim()
        println commit_id

        stage "build"
        def app = docker.build "test"

        stage "publish"
        app.push 'master'
        app.push "${commit_id}"
    }
}
