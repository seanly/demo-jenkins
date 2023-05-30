# jenkins

## init

```bash
curl -XPOST  -H "Content-Type: application/x-yaml" -H "$(curl -s 'http://<jenkins_url>/crumbIssuer/api/xml?xpath=concat(//crumbRequestField,":",//crumb)')" --data-binary @jenkins.yaml http://<jenkins_url>/configuration-as-code/apply

# -u "<username>:<api_token>" 认证参数
```

## backup

```bash
tar -cvzf /tmp/jenkins_home.tar.gz \
  --exclude=jobs --exclude=plugins \
  --exclude=workspace --exclude=workflow-libs \
  --exclude=monitoring --exclude=fingerprints \
  --exclude=jenkins_home/war --exclude=logs \
  --exclude=jenkins-slave-* \
  --exclude=.java --exclude=.cache --exclude=.fonts \
  --exclude=groovy \
  /var/jenkins_home
```

