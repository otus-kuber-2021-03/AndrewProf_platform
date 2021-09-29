Установил kubectl-debug
Установил daemonset манифеста:

$ kubectl apply -f https://raw.githubusercontent.com/aylei/kubectl-debug/master/scripts/agent_daemonset.yml

На тестовом поде  выполнил strace:
$ kubectl debug nginx --image alpine:latest -it target nginx -- /bin/sh
Без ошибок
