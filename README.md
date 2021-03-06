This is a complete fork of a work originally done by Google Inc. at
https://github.com/google/google-java-format.

The aim is to get some additions to Google Java Style implemented and so these
changes are not intended for contribution back to the original repository as
there is mostly no chance that they will be accepted there. At the same time,
this fork is intended to be fully synchronized with the original repository
and it follows their version numbers.

# google-java-format

`google-java-format` is a program that reformats Java source code to comply with
[Google Java Style][].

[Google Java Style]: https://google.github.io/styleguide/javaguide.html

## Using the formatter

### from the command-line

[Download the formatter](https://github.com/qbixus/google-java-format/releases)
and run it with:

```
java -jar /path/to/google-java-format-1.5-all-deps.jar <options> [files...]
```

The formatter can act on whole files, on limited lines (`--lines`), on specific
offsets (`--offset`), passing through to standard-out (default) or altered
in-place (`--replace`).

To reformat changed lines in a specific patch, use
[`google-java-format-diff.py`](https://github.com/qbixus/google-java-format/blob/master/scripts/google-java-format-diff.py).

***Note:*** *There is no configurability as to the formatter's algorithm for
formatting. This is a deliberate design decision to unify our code formatting on
a single format.*

### IntelliJ

~~A [google-java-format IntelliJ
plugin](https://plugins.jetbrains.com/plugin/8527) is available from the plugin
repository.~~

The plugin will not be enabled by default. To enable it in the current project,
go to "File→Settings...→google-java-format Settings" and check the "Enable"
checkbox.

To enable it by default in new projects, use "File→Other Settings→Default
Settings...".

When enabled, it will replace the normal "Reformat Code" action, which can be
triggered from the "Code" menu or with the Ctrl-Alt-L (by default) keyboard
shortcut.

### Eclipse

A [google-java-format Eclipse
plugin](https://github.com/qbixus/google-java-format/releases/download/google-java-format-1.5/google-java-format-eclipse-plugin-1.5.0.jar)
can be downloaded from the releases page. Drop it into the Eclipse [drop-ins
folder](http://help.eclipse.org/neon/index.jsp?topic=%2Forg.eclipse.platform.doc.isv%2Freference%2Fmisc%2Fp2_dropins_format.html)
to activate the plugin.

The plugin adds a `google-java-format` formatter implementation that can be
configured in `Window > Preferences > Java > Code Style > Formatter > Formatter
Implementation`.

### as a library

The formatter can be used in software which generates java to output more
legible java code. Just include the library in your maven/gradle/etc.
configuration.

#### Maven

```xml
<dependency>
  <groupId>com.github.qbixus</groupId>
  <artifactId>google-java-format</artifactId>
  <version>1.5</version>
</dependency>
```

#### Gradle

```groovy
dependencies {
  compile 'com.github.qbixus:google-java-format:1.5'
}
```

You can then use the formatter through the `formatSource` methods. E.g.

```java
String formattedSource = new Formatter().formatSource(sourceString);
```

or

```java
CharSource source = ...
CharSink output = ...
new Formatter().formatSource(source, output);
```

Your starting point should be the instance methods of
`com.google.googlejavaformat.java.Formatter`.

## Building from source

    mvn install

## License

```text
Copyright 2015 Google Inc.
Copyright 2017 Denis Zenin

Licensed under the Apache License, Version 2.0 (the "License"); you may not
use this file except in compliance with the License. You may obtain a copy of
the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS, WITHOUT
WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the
License for the specific language governing permissions and limitations under
the License.
```
