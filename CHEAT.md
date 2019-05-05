# fultonj cheat sheet

This is how I keep my branch and fork updated and push changes back

## Get my fork
```
git clone git@github.com:fultonj/tripleo-lab.git
cd tripleo-lab
```

## Update it with the latest from upstream

- Add remote from original repository in my forked repository:
```
git remote add upstream git://github.com/cjeanner/tripleo-lab.git
git fetch upstream
```
- Update my fork from original repo to keep up with changes:
```
git pull upstream master
git push
```

## Use it
```
ansible -i inventory.yaml -m ping builder
ansible-playbook -i inventory.yaml builder.yaml --skip-tags validations,metrics
```

