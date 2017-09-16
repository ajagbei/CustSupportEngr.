# CustSupportEngr.........Solution.
Case 1: PRODSUP-001:


Hi. I am trying to get my test cases to show up on CircleCI but it is not working. I have a fork of this project in my github account https://github.com/mtedone/podam. I added the project to CircleCI and got a green build but the Test Results tab is empty

---

Harry

=====================================================================

Case 1: PRODSUP-001:

Hi Harry,

I've checked your issue and here is my conclusion:
1) CircleCI is case-sensitive , so you need to rename your Circle.yml to  circle.yml
2) You need to enable Maven Surefire Plugin in pov.xml file in root dir
just remove below code at line 279:

<configuration>
   <skip>true</skip>
</configuration>


3) You need clear you circle.yml file and add below lines:

test:
  post:
    - mkdir -p $CIRCLE_TEST_REPORTS/junit/
    - find . -type f -regex ".*/target/surefire-reports/.*xml" -exec cp {} $CIRCLE_TEST_REPORTS/junit/ \;



More information is available here:
https://circleci.com/docs/test-metadata#metadata-collection-in-custom-test-steps

You also may check my changes at https://github.com/ajagbei/CustSupportEngr.
