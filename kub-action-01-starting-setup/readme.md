docker build -t kub-first-app .

docker tag kub-first-app lourranio/kub-first-app

docker push lourranio/kub-first-app

kubectl create deployment first-app --image=lourranio/kub-first-app