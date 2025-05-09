# Release Checker - API
Easy to use and lightweight api for notify about new release version from GitHub

## Table of Contentes

1. [About](#About)
2. [Short Wiki](#Short-Wiki)
   * [Method Summary](#Method-Summary)
   * [Errors](#Errors)
   * [Working Example](#Working-Example)
3. [Libraries and API's](#libraries-and-apis)
4. [Installation](#Installation)
5. [Contributing](#contributing)
6. [ToDo](#ToDo)
7. [License](#License)

## About

This api works by getting releases versions via GitHub API, using link 
`https://api.github.com/repos/[REPOSITORY AUTHOR]/[REPOSITORY NAME]/releases"`.

The methods described in [Method Summary](#Method-Summary), modify the values of the variables,
```java
private static String version;
private static String repositoryURL;
```
coded in API. This API uses jsonSimple library to work, maven dependency is in [Installation](#Installation)*. 
In case of errors with API please describe it in Issues.


## Short Wiki
### Method Summary

| Type    | Method                                                      | Description                        |
|---------|-------------------------------------------------------------|------------------------------------|
| String  | getVersion(**String** version)                              | Get the latest release version     |
| String  | getRepository(**String** author, **String** repositoryName) | Get the author and repository name |
| boolean | releaseCheck()                                            | Gets state of latest release       |


### Errors

| Message                                                                                  | Reason                                       |
|------------------------------------------------------------------------------------------|----------------------------------------------|
| `[ERROR] Assign a version using getVersion(). Setting default value as FALSE.`           | You need to specify a version of release     |
| `[ERROR] Assign a repository URL using getRepository(). Setting default value as FALSE.` | You need to specify a repository and release |
| `java.lang.IndexOutOfBoundsException: Index 0 out of bounds for length 0`                | There is no releases in that repository      |

### Working Example

```java
public static void main(String[] args) {
  getVersion("v2.0");
  getRepository("zappygamingyt", "xorencrypt");
  if (releaseCheck()) {
    System.out.println("There is no new versions");
  }
  else {
    System.out.println("There is new version");
  }
}
```

## Libraries and API's

* [JSONSimple](https://mvnrepository.com/artifact/com.googlecode.json-simple/json-simple)
* [GitHubAPI](https://docs.github.com/)
* [JitPack](https://jitpack.io/)

## Installation
Add this to your maven project in `pom.xml` file:

```xml
<repositories>
    <repository>
        <id>jitpack.io</id>
        <url>https://jitpack.io</url>
    </repository>
</repositories>
```
Compile scope is very important If you don't want to add dependencies manually or by using external jar files:
```xml
<dependency>
    <groupId>com.github.ZappyGamingYT</groupId>
    <artifactId>releasesChecker-API</artifactId>
    <version>v1.2.1</version>
    <scope>compile</scope>
</dependency>
```
<span style="color:#e00010"><b>* For v1.2.1, adding jsonSimple dependency is not required:</b></span>
```xml
<dependency>
    <groupId>com.googlecode.json-simple</groupId>
    <artifactId>json-simple</artifactId>
    <version>1.1.1</version>
</dependency>
```

## Contributing
Pull requests are always welcome. For bigger changes, please open an issue first to discuss what you would like to change.

## ToDo
* For now, we do not expect another versions.

## License
[GNU GPLv3](https://choosealicense.com/licenses/gpl-3.0/)
