# For take orch build have to run in SRC folder
cd gradle-convention-plugins && git checkout develop && git pull &&  gradle publishToMavenLocal && cd - \
                && cd bom && git checkout develop && git pull &&  gradle publishToMavenLocal && cd - \
                && cd i18n && git pull &&  gradle publishToMavenLocal && cd - \
                && cd di &&  gradle publishToMavenLocal && cd - \
                && cd jsonschema/javaModuleExporter && git pull &&  gradle publishToMavenLocal && cd - \
                && cd domain-model && git checkout develop && git pull &&  gradle publishToMavenLocal && cd - \
                && cd utils && git checkout develop && git pull &&  gradle publishToMavenLocal && cd - \
                && cd exceptions && git pull &&  gradle publishToMavenLocal && cd - \
                && cd otpclient &&  git checkout develop && gradle publishToMavenLocal && cd - \
                && cd logclient && git checkout develop && git pull &&  gradle publishToMavenLocal && cd - \
                && cd validator && git checkout develop && git pull &&  gradle publishToMavenLocal && cd - \
                && cd microservice && git checkout develop && git pull &&  gradle publishToMavenLocal && cd - \
                && cd api-model && git checkout develop && git pull &&  gradle publishToMavenLocal && cd - \
                && cd dao && git checkout develop && git pull &&  gradle publishToMavenLocal && cd - \
                && cd mail && git checkout develop && git pull &&  gradle publishToMavenLocal && cd - \
                && cd pkiclient && git checkout develop && git pull &&  gradle publishToMavenLocal && cd - \
                && cd auditlog && git checkout develop && git pull &&  gradle publishToMavenLocal && cd - \
                && cd quartz-mongodb &&  git pull &&  gradle publishToMavenLocal && cd -\
                && cd orch-apisix-client && git checkout develop && git pull &&  gradle publishToMavenLocal && cd -`