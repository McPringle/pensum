# Pensum

[![All Tests](https://github.com/McPringle/pensum/actions/workflows/all-tests.yml/badge.svg)](https://github.com/McPringle/pensum/actions/workflows/all-tests.yml)

**Your office in a pocket.**

## Features

### Manage todos

## Build

### Maven

*Pensum* uses [Maven](https://maven.apache.org/) to build the project. Please use standard Maven commands to build what you need:

| Command          | What it does                                                      |
|------------------|-------------------------------------------------------------------|
| `./mvnw`         | compile and run the app                                           |
| `./mvnw clean`   | cleanup generated files and build artefacts                       |
| `./mvnw compile` | compile the code without running the tests                        |
| `./mvnw test`    | compile and run all tests                                         |
| `./mvnw package` | compile, test, and create a JAR file to run it with Java directly |
| `./mvnw verify`  | compile, test, package, and run analysis tools                    |

There is *no need* to run the `install` or `deploy` tasks. They will just run longer, produce unnecessary output, burn energy, and occupy your disk space. [Don't just blindly run mvn clean install...](https://www.andreaseisele.com/posts/mvn-clean-install/)

### Docker

*Pensum* comes with a complete dockerized build for production use. It is not recommended to use the self-contained build for development purposes. Please take a look at the section about [Production Build](#production-build) below.

## Running and debugging

### Running from the command line

To run from the command line, run `./mvnw` and open http://localhost:8080 in your browser.

### Running and debugging in Intellij IDEA

- Locate the `Application.java` class in the project view. It is in the `src` folder, under the main package's root.
- Right-click on the `Application` class
- Select "Debug 'Application.main()'" from the list

After the server has started, you can view the UI at http://localhost:8080/ in your browser.
You can now also attach breakpoints in code for debugging purposes, by clicking next to a line number in any source file.

### Running and debugging in Eclipse

- Locate the `Application.java` class in the package explorer. It is in `src/main/java`, under the main package.
- Right-click on the file and select `Debug As` --> `Java Application`.

Do not worry if the debugger breaks at a `SilentExitException`. This is a Spring Boot feature and happens on every startup.

After the server has started, you can view it at http://localhost:8080/ in your browser.
You can now also attach breakpoints in code for debugging purposes, by clicking next to a line number in any source file.

## Configuration

*Pensum* can be started without any specific configuration. All configuration options have working default values. To modify these default values just specify environment variables with the following names:

| Variable | Default | Description                                       |
|----------|---------|---------------------------------------------------|
| TZ       | UTC     | The timezone used for date and time calculations. |

## Production

### Production Build

#### Maven

You can use [Maven](https://maven.apache.org/) to build *Pensum* for production. Just specify the `production` profile. Example:

```shell
./mvnw clean package -Pproduction
```

#### Docker

To create a production build for *Pensum* it is highly recommended to use [Docker](https://www.docker.com/) or [Podman](https://podman.io/). *Pensum* comes with a complete dockerized self-contained build. You don't need to have Maven or Java installed, [Docker](https://www.docker.com/) or [Podman](https://podman.io/) is enough. The Docker build file contains everything needed, just start a standard Docker build with the following command:

```shell
docker build -t pensum .
```

This might run for a while and will produce a Docker image tagged `pensum` on your local system.

### Run in Production

It is highly recommended to use [Docker](https://www.docker.com/) or [Podman](https://podman.io/) to run *Pensum* in production. Use the following command line as an example:

```shell
docker run \
    --name pensum \
    -p 80:8080 \
    -e TZ=CET \
    -d \
    --rm \
    mcpringle/pensum
```

Short explanation, consult the Docker or Podman documentation for more information about all available options for running an image.

| Option           | Explanation                                     |
|------------------|-------------------------------------------------|
| --name pensum    | Specify the name for the running instance.      |
| -p 80:8080       | Make *Pensum* available on host port 80         |
| -e KEY=value     | Configure *Pensum* using environment variables. |
| -d               | Run *Pensum* in daemon mode (background).       |
| --rm             | Remove the container when stopping *Pensum*.    |
| mcpringle/pensum | The Docker image to be started.                 |

Modify this command according your needs and consult the [configuration section](#configuration) above for more information about how to configure *Pensum*. The Docker image of *Pensum* will be pulled from [Docker Hub](https://hub.docker.com/) automatically when not available locally.

## Communication

### Matrix Chat

There is a channel at Matrix for quick and easy communication. This is publicly accessible for everyone. For developers as well as users. The communication in this chat is to be regarded as short-lived and has no documentary character.

You can find our Matrix channel here: [@project-pensum:ijug.eu](https://matrix.to/#/%23project-pensum:ijug.eu)

### GitHub Discussions

We use the corresponding GitHub function for discussions. The discussions held here are long-lived and divided into categories for the sake of clarity. One important category, for example, is that for questions and answers.

Discussions on GitHub: https://github.com/McPringle/pensum/discussions  
Questions and Answers: https://github.com/McPringle/pensum/discussions/categories/q-a

## Contributors

Special thanks for all these wonderful people who had helped this project so far ([emoji key](https://allcontributors.org/docs/en/emoji-key)):

<!-- ALL-CONTRIBUTORS-LIST:START - Do not remove or modify this section -->
<!-- prettier-ignore-start -->
<!-- markdownlint-disable -->
<table>
  <tbody>
    <tr>
      <td align="center" valign="top" width="14.28%"><a href="https://github.com/McPringle"><img src="https://avatars.githubusercontent.com/u/1254039?v=4?s=100" width="100px;" alt="Marcus Fihlon"/><br /><sub><b>Marcus Fihlon</b></sub></a><br /><a href="#projectManagement-McPringle" title="Project Management">📆</a> <a href="#ideas-McPringle" title="Ideas, Planning, & Feedback">🤔</a> <a href="https://github.com/McPringle/pensum/commits?author=McPringle" title="Code">💻</a> <a href="#design-McPringle" title="Design">🎨</a></td>
    </tr>
  </tbody>
</table>

<!-- markdownlint-restore -->
<!-- prettier-ignore-end -->

<!-- ALL-CONTRIBUTORS-LIST:END -->

## Contributing

### Good First Issues

For your first contribution to this repository, you can take a look at the issues listed here: [good first issue](https://github.com/McPringle/pensum/labels/good%20first%20issue).

## Copyright and License

[AGPL License](https://www.gnu.org/licenses/agpl-3.0.de.html)

*Copyright (C) Marcus Fihlon and the individual contributors to **Pensum**.*

This program is free software: you can redistribute it and/or modify it under the terms of the GNU Affero General Public License as published by the Free Software Foundation, either version 3 of the License, or (at your option) any later version.

This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the GNU Affero General Public License for more details.

You should have received a copy of the GNU Affero General Public License along with this program.  If not, see <http://www.gnu.org/licenses/>.
