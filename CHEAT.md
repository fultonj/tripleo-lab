# fultonj cheat sheet

This is how I keep my branch and fork updated and push changes back

## Get my fork
```
git clone git@github.com:fultonj/tripleo-lab.git
cd tripleo-lab
```

## Update my fork's master from upstream

- Add remote from original repository in my forked repository:
```
git checkout master
git remote add upstream git://github.com/cjeanner/tripleo-lab.git
git fetch upstream
```
- Update my fork from original repo to keep up with changes:
```
git pull upstream master
git push
```

## Update my branch from latest master
- Review changes to be applied (excluding docs)
```
git diff master fultonj  -- . ':(exclude)*.md'
```
- Resolve conflicts manually during rebase.
```
git checkout fultonj
git rebase -i master
git pull
git push
```

## Use it
```
ssh-add -l
ansible -i inventory.yaml -m ping builder
ansible-playbook -i inventory.yaml builder.yaml -e @environments/podman.yaml --skip-tags validations,metrics
```

## Destroy it
```
sudo /usr/local/bin/lab-destroy
```
