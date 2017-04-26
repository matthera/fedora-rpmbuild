docker.withRegistry('http://localhost:5000/') {
  node ("sandy") {
    stage ("Checkout") {
      dir ("scm") {
        git "https://github.com/matthera/fedora-rpmbuild"
        def version = sh script: "git describe", returnStdout: true
      }
    }
    stage ("Build Image") {
      def mock = docker.build "matthera/fedora-rpmbuild:${version}", "scm/fedora-rpmbuild"
    }
    stage ("Push Image") {
      mock.push();
    }
  }
}
