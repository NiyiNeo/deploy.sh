# deploy.sh
This repository is for serverless website. Pod 2

#!/bin/bash
 
ENV=$1
 
if [ "$ENV" == "dev" ]; then
  BUCKET=pod-milestone2-stack-1747065639.dev.vitality.luitprojects.com 
  DIST_ID=E3G2B2NO54HKPQ
elif [ "$ENV" == "prod" ]; then
  BUCKET=pod-milestone2-stack-1747065639.vitality.luitprojects.com
  DIST_ID=E1WKZR1LGS2JKL
else
  echo "Usage: ./deploy.sh [dev|prod]"
  exit 1
fi
 
echo "Deploying to $ENV environment..."
aws s3 sync ./dist s3://$BUCKET --delete
#aws cloudfront create-invalidation --distribution-id $DIST_ID --paths "/*"
echo "Deployment to $ENV completed."
