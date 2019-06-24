# Drone

## Pipeline Configuration File
Drone's Configuration File is a `.drone.yml`, there are two versions I've encountered: version 0.8 and version 1.0. This is focused on version 1.0.

The configuration file may consist of the `kind`, `name`, `steps`, and `platform` at the root-level.

#### Steps
You can add the [`steps`](https://docs.drone.io/user-guide/pipeline/steps/) at the top-level. Each `step` may consist of `name`, `image`, `commands`, `when`, `settings` (used for plugins afaik).

> Each step starts a new container that includes a clone of your repository, and then runs the contents of your commands section inside it.

Each step is under the `steps` prop and are separated by `-` before the `name`.

| Prop | Known Enums |
| ------------- |:-------------:|
| `image` | `golang`, `node`, `plugins/slack` (*Plugins) |
| `arch` | `amd64`, `arm64` |

#### Plugins
> Plugins are *docker containers* that encapsulate commands, and can be shared and re-used in your pipeline. Examples of plugins include sending Slack notifications, building and publishing Docker images, and uploading artifacts to S3.

#### Platform
Defines the operating system and architecture for the container the steps will run on. May consist of `os` and `arch`

| Prop | Known Enums |
| ------------- |:-------------:|
| `os` | `windows`, `linux` |
| `arch` | `amd64`, `arm64` |