docker.withRegistry('http://localhost:5000/') {
  node ("sandy") {
    stage ("Checkout") {
      dir ("scm") {
        git "https://github.com/matthera/fedora-rpmbuild"
        ver = sh(script: "git describe", returnStdout: true).trim()
      }
    }
    stage ("Build Image") {
      mock = docker.build "matthera/fedora-rpmbuild:${ver}", "scm"
    }
    stage ("Push Image") {
      mock.push();
    }
  }
}
