# Jacoco

Sign up in codecov.io with your own github account.

Github actions workflow:

```
coverage:
    needs: [run_tests_build_app]
    runs-on: ubuntu-20.04
    steps:
      - name: Clone repository
        uses: actions/checkout@v2
      - name: Set up JDK 11
        uses: actions/setup-java@v1
        with:
          java-version: 11
      - name: Generate tests
        run: mvn -B verify --no-transfer-progress
      - name: Upload coverage reports
      - uses: codecov/codecov-action@v2
        with:
          file: ./**/target/site/jacoco/jacoco.xml
          name: codecov 
```

`pom.xml`

```
            <plugin>
				<groupId>org.jacoco</groupId>
				<artifactId>jacoco-maven-plugin</artifactId>
				<version>0.8.7</version>
				<executions>
					<!-- Prepares the property pointing to the JaCoCo runtime agent which 
						is passed as VM argument when Maven the Surefire plugin is executed. -->
					<execution>
						<goals>
							<goal>prepare-agent</goal>
						</goals>
					</execution>
					<!-- Ensures that the code coverage report is created after all tests 
						have been run. -->
					<execution>
						<id>generate-report</id>
						<goals>
							<goal>report</goal>
						</goals>
					</execution>
				</executions>
			</plugin>
```

Generate reports with: 

`mvn jacoco:report`

Report will be generated in `target/site/jacoco/index.html`