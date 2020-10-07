# PR
Open your pull request from the command line.

Add below to your bash profile, then type `pr` from your command line and watch your browser open to the PR

```bash
# get current git branch
branch() {
    cat .git/HEAD | sed -ne 's/ref: refs\/heads\///p'
}
# open git pull request page for current repo and branch
pr() {
    url=$(git remote -v | awk '/fetch/{print $2}' | sed -Ee 's#(git@|git://)#https://#' -e 's@com:@com/@' -e 's%\.git$%%' | sed 's/\(.*\):/\1\//')
    open "${url}"/pull/new/$(branch)
}
```
