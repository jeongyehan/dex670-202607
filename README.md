# Anypoint Platform Development: Production-Ready Integrations - DEX670

## Local Path
- PROJECT_HOME=/Users/yehan.jeong/Desktop/dex670-202607
- STUDENT_FILE=/Users/yehan.jeong/Desktop/MuleSoft/CDEV-DEX670-EN-25oct2024-Student-Files

## Anypoint Platform Information
- Mule Account: yehan202607

### Business Group
- Business Group ID: 1adb85d2-035b-4e2c-a931-420f7396c267

### Connected App
- Exchange Viewer ID: 088002863bcc444fba668e266c6d6cd3
- Exchange Viewer Secret: a61E5A9b283f4e68940f2F0a59194e23
- Exchange Contributor ID: b5c8d0d3077543b0a306334663ba56c5
- Exchange Contributor Secret: bff198B51DAD4C1Ebc9ee32Eb31D4a4E

## Commands
- export PROJECT_HOME=/Users/yehan.jeong/Desktop/dex670-202607
- export STUDENT_FILE=/Users/yehan.jeong/Desktop/MuleSoft/CDEV-DEX670-EN-25oct2024-Student-Files
- echo $PROJECT_HOME
- echo $STUDENT_FILE
- cp $STUDENT_FILE/etc/settings.xml ~/.m2/
- cd $PROJECT_HOME
- mkdir bom
- mkdir parent-pom
- cp $STUDENT_FILE/walkthroughs/devint/module01/wt1-1_starter/bom/pom.xml ./bom/pom.xml
- cp $STUDENT_FILE/walkthroughs/devint/module01/wt1-1_starter/parent-pom/pom.xml ./parent-pom/pom.xml
- cd $PROJECT_HOME
- mvn install:install-file -Dfile=bom/pom.xml -DpomFile=bom/pom.xml
- mvn install:install-file -Dfile=parent-pom/pom.xml -DpomFile=parent-pom/pom.xml
- cd $PROJECT_HOME
- cp -r $STUDENT_FILE/walkthroughs/devint/module01/wt1-1_starter/apps-commons ./
- cd $PROJECT_HOME/apps-commons
- mvn clean install
- cd $PROJECT_HOME
- cp -r $STUDENT_FILE/walkthroughs/devint/module01/wt1-1_starter/check-in-papi ./
- cd $PROJECT_HOME/check-in-papi
- mvn clean verify -U -Dencrypt.key=secure12345 -DskipTests=true
- -M-Dencrypt.key=secure12345 -M-Danypoint.platform.gatekeeper=disabled
- curl -ik -X PUT -H "Content-Type: application/json" -d "{\"lastName\" :\"Smith\",\"numBags\":2}" https://localhost:8081/api/v1/tickets/PNR123/checkin
- curl -ik -X PUT -H "Content-Type: application/json" -d "{\"payerID\": \"STJ8222K092ST\", \"paymentID\": \"PAY-1AKD7482FAB9STATKO\"}" https://localhost:8081/api/v1/tickets/N123/paymentApproval
- curl -ik https://localhost:8081/alive
- curl -ik https://localhost:8081/ready
