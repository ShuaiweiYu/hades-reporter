`docker build . -t ghcr.io/shuaiweiyu/hades-reporter:latest`

`docker push ghcr.io/shuaiweiyu/hades-reporter:latest`

```
{
  "name": "Example Job",
  "metadata": {
    "GLOBAL": "test"
  },
  "timestamp": "2021-01-01T00:00:00.000Z",
  "priority": 3, // optional, default 3
  "steps": [
    {
      "id": 1, // mandatory to declare the order of execution
      "name": "Clone",
      "image": "ghcr.io/ls1intum/hades/hades-clone-container:latest", // mandatory
      "metadata": {
        "REPOSITORY_DIR": "/shared",
        "HADES_TEST_USERNAME": "{{user}}",
        "HADES_TEST_PASSWORD": "{{password}}",
        "HADES_TEST_URL": "{{test_repo}}",
        "HADES_TEST_PATH": "./example",
        "HADES_TEST_ORDER": "1",
        "HADES_ASSIGNMENT_USERNAME": "{{user}}",
        "HADES_ASSIGNMENT_PASSWORD": "{{password}}",
        "HADES_ASSIGNMENT_URL": "{{assignment_repo}}",
        "HADES_ASSIGNMENT_PATH": "./example/assignment",
        "HADES_ASSIGNMENT_ORDER": "2"
      }
    },
    {
      "id": 2, // mandatory to declare the order of execution
      "name": "Execute",
      "image": "ls1tum/artemis-maven-template:java17-18", // mandatory
      "script": "set +e && cd ./shared/example || exit 0 && ./gradlew --status || exit 0 && ./gradlew clean test || exit 0"
    },
    {
      "id": 3,
      "name": "Result",
      "image": "ghcr.io/shuaiweiyu/hades-result-parser:latest",
      "metadata": {
        "API_ENDPOINT": "https://hades-benchmarker.wei-tech.site/v1/result",
        "INGEST_DIR":"./shared/example",
        "HADES_TEST_PATH": "./example",
        "HADES_ASSIGNMENT_PATH": "./example/assignment"
      }
    }
  ]
}
```

```
{
  "name": "Example Job",
  "metadata": {
    "GLOBAL": "test"
  },
  "timestamp": "2021-01-01T00:00:00.000Z",
  "priority": 3, // optional, default 3
  "steps": [
    {
      "id": 1, // mandatory to declare the order of execution
      "name": "Clone",
      "image": "ghcr.io/ls1intum/hades/hades-clone-container:latest", // mandatory
      "metadata": {
        "REPOSITORY_DIR": "/shared",
        "HADES_TEST_USERNAME": "{{user}}",
        "HADES_TEST_PASSWORD": "{{password}}",
        "HADES_TEST_URL": "{{test_repo}}",
        "HADES_TEST_PATH": "./example",
        "HADES_TEST_ORDER": "1",
        "HADES_ASSIGNMENT_USERNAME": "{{user}}",
        "HADES_ASSIGNMENT_PASSWORD": "{{password}}",
        "HADES_ASSIGNMENT_URL": "{{assignment_repo}}",
        "HADES_ASSIGNMENT_PATH": "./example/assignment",
        "HADES_ASSIGNMENT_ORDER": "2"
      }
    },
    {
      "id": 2,
      "name": "Report Starting Time",
      "image": "ghcr.io/shuaiweiyu/hades-reporter:latest",
      "metadata": {
        "ENDPOINT": "https://hades-benchmarker.wei-tech.site/v1/start_time"
      }
    },
    {
      "id": 3, // mandatory to declare the order of execution
      "name": "Execute",
      "image": "ls1tum/artemis-maven-template:java17-18", // mandatory
      "script": "set +e && cd ./shared/example || exit 0 && ./gradlew --status || exit 0 && ./gradlew clean test || exit 0"
    },
    {
      "id": 4,
      "name": "Result",
      "image": "ghcr.io/shuaiweiyu/hades-result-parser:latest",
      "metadata": {
        "API_ENDPOINT": "https://hades-benchmarker.wei-tech.site/v1/result",
        "INGEST_DIR":"./shared/example",
        "HADES_TEST_PATH": "./example",
        "HADES_ASSIGNMENT_PATH": "./example/assignment"
      }
    }
  ]
}
```

```
{
  "name": "Example Job",
  "metadata": {
    "GLOBAL": "test"
  },
  "timestamp": "2021-01-01T00:00:00.000Z",
  "priority": 3, // optional, default 3
  "steps": [
    {
      "id": 1, // mandatory to declare the order of execution
      "name": "Clone",
      "image": "ghcr.io/ls1intum/hades/hades-clone-container:latest", // mandatory
      "metadata": {
        "REPOSITORY_DIR": "/shared",
        "HADES_TEST_USERNAME": "{{user}}",
        "HADES_TEST_PASSWORD": "{{password}}",
        "HADES_TEST_URL": "{{test_repo}}",
        "HADES_TEST_PATH": "./example",
        "HADES_TEST_ORDER": "1",
        "HADES_ASSIGNMENT_USERNAME": "{{user}}",
        "HADES_ASSIGNMENT_PASSWORD": "{{password}}",
        "HADES_ASSIGNMENT_URL": "{{assignment_repo}}",
        "HADES_ASSIGNMENT_PATH": "./example/assignment",
        "HADES_ASSIGNMENT_ORDER": "2"
      }
    },
    {
      "id": 2,
      "name": "Report Starting Time",
      "image": "ghcr.io/shuaiweiyu/hades-reporter:latest",
      "metadata": {
        "ENDPOINT": "https://hades-benchmarker.wei-tech.site/v1/start_time"
      }
    },
    {
      "id": 3, // mandatory to declare the order of execution
      "name": "Execute",
      "image": "ls1tum/artemis-maven-template:java17-18", // mandatory
      "script": "set +e && cd ./shared/example || exit 0 && ./gradlew --status || exit 0 && ./gradlew clean test || exit 0"
    }
  ]
}
```


```
{
  "name": "Example Job",
  "metadata": {
    "GLOBAL": "test"
  },
  "timestamp": "2021-01-01T00:00:00.000Z",
  "priority": 3, // optional, default 3
  "steps": [
    {
      "id": 1, // mandatory to declare the order of execution
      "name": "Clone",
      "image": "ghcr.io/ls1intum/hades/hades-clone-container:latest", // mandatory
      "metadata": {
        "REPOSITORY_DIR": "/shared",
        "HADES_TEST_USERNAME": "{{user}}",
        "HADES_TEST_PASSWORD": "{{password}}",
        "HADES_TEST_URL": "{{test_repo}}",
        "HADES_TEST_PATH": "./example",
        "HADES_TEST_ORDER": "1",
        "HADES_ASSIGNMENT_USERNAME": "{{user}}",
        "HADES_ASSIGNMENT_PASSWORD": "{{password}}",
        "HADES_ASSIGNMENT_URL": "{{assignment_repo}}",
        "HADES_ASSIGNMENT_PATH": "./example/assignment",
        "HADES_ASSIGNMENT_ORDER": "2"
      }
    },
    {
      "id": 2, // mandatory to declare the order of execution
      "name": "Execute",
      "image": "ls1tum/artemis-maven-template:java17-18", // mandatory
      "script": "set +e && cd ./shared/example || exit 0 && ./gradlew --status || exit 0 && ./gradlew clean test || exit 0"
    },
    {
      "id": 3,
      "name": "Report Starting Time",
      "image": "ghcr.io/shuaiweiyu/hades-reporter:latest",
      "metadata": {
        "ENDPOINT": "https://hades-benchmarker.wei-tech.site/v1/start_time"
      }
    }
  ]
}
```