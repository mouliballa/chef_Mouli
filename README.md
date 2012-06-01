<!-- # Overview -->
# 概要

<!--
Welcome to Chef Fundamentals. This is the source training material
repository for the class. The materials themselves are written in
plain text "[Markdown](http://daringfireball.net/projects/markdown/)"
format, and presented using the
"[ShowOff](https://github.com/schacon/showoff)" Ruby-based presentation
application.
-->

Chefの基礎ドキュメントにようこそ。
これは、トレーニングクラスで使用するマテリアルのソースです。
マテリアルは、プレーンテキスト"[Markdown](http://daringfireball.net/projects/markdown/)"のフォーマットで記述し、
"[ShowOff](https://github.com/schacon/showoff)"という Ruby-based プレゼンアプリケーションで表示しています。

<!--
If you're seeing this at http://localhost:9090, you need to run the
`showoff` command from the `slides` directory.
-->

もしもこのページがhttp://localhost:9090にアクセスして見えているなら、
`showoff`コマンドを`slides`ディレクトリで実行してください。

<!-- # Setup -->
#セットアップ

<!-- Requirements: -->
必要条件：

* Ruby 1.8.7+
* RubyGems 1.3.7+
* Rake
* libxml2 and libxslt development headers (e.g., libxml2-dev and
  libxslt-dev on Debian/Ubuntu).

```
gem install bundler
bundle install
rake present # runs bundle exec showoff serve in the slides dir
```

<!--
Depending on how your local system's Ruby was installed, you may need
to use `sudo` to run `gem install` and `bundle install`. You may also
need to use `bundle exec showoff serve` in the `slides` directory to
run the presentation, though the rake task should handle this already.
-->

システムにRubyがどのようにインストールされているかによっては、
`sudo`を使って`gem install`と`bundle install`を実行する必要があります。
更にrakeタスクで次のコマンドが実行されているはずにもかかわらず、
別途`slide`のディレクトリで`bundle exec showoff serve`を実行する必要がある場合もあります。

<!-- Two URLs are available: -->
2種類のURLがあります:

* http://localhost:9090 - "student" view of the slides
* http://localhost:9090/presenter - "presenter" view of the slides

<!--
When presenting the materials as an instructor, use the "presenter"
view. This will also pop up a second browser window that will advance
with the presenter window. To move forward and back, use the arrow
keys. Down/Right go forward, Up/Left go backward. Spacebar will also
advance slides forward.
-->

講師としてこのマテリアルを使用している時は、"presenter"のビューを使用してください。
この画面では、プレゼンター用に表示枠を追加します。
スライドを前後に移動するためには、キーボードの矢印キーを使用します。
Down/Rightで前進, Up/Leftで後退します。
Spacebarでもスライドを前進させることができます。　　　　　

<!-- # Installed Gems -->
# Gemのインストール

<!--
The source materials in the `slides` directory are set up as a showoff
project. As such, the `showoff` gem is required. In order to generate
PDFs with showoff, the `pdfkit` gem is installed.
-->

`slide`ディレクトリ以下のマテリアルは、showoffのプロジェクトして設定されています。
従って、プレゼンテーションの表示には、`showoff`が必要ないなります。
`showoff`でPDFファイルを生成する場合は、`pdfkit`がインストールされている必要があります。

<!--
Also, the instructor lab setup will use Chef and the Knife EC2 plugin,
so those gems are included as well.
-->

更に講師が使用する環境では、ChefとKnife EC2のpluginを使いますので、それらのインストールも必要です。

<!-- *Do not* commit `Gemfile.lock` to the repository. -->
リポジトリーに`Gemfile.lock`を*コミットしない*でください。

**Note** The current release of ShowOff doesn't include some pull
  requests adding features that we liked, so the showoff gem is
  installed from a separate repository.

**Note** 現リリースのshowoffは、私たちが期待するようなpullリクエストの追加機能を持っていません。
従って、showoffのgemを別のリポジトリーインストールしています。 

<!-- # Slides Directory -->
# Slideのディレクトリ

<!-- Most of the action happens in the slides directory. -->
大抵の作業はこのディレクトリ以下で行います。

## Rakefile

<!--
The `slides/Rakefile` has a task to set up the directory and an
initial `01_slide.md` file for the specified section.
-->

`slides/Rakefile`は、そのディレクトリを設定すると同時に、
それぞれのセクションの`01_slide.md`を設定します。

    rake mksection SECTION=just-enough-ruby-for-chef
    ** Creating section just-enough-ruby-for-chef **
    - populating 01_slide.md

This does not add the section to `showoff.json`. When contributing a new
section, do not add it to the `showoff.json` file, as that should be
reviewed before modifying the base course for everyone.

<!-- ## Slide Style Guide -->
## Slideのスタイルに関するガイド

<!-- This is spartan and will be embellished. -->
現在は、最低限の修飾のみです。いづれ改善する予定です。

<!--
* Create sections as directories.
* Use PNGs for images.
* Directory names should be lower case words as a title, "getting-started"
* Each directory should have a 01_slide.md, multiple sections may be
  broken up later.
-->

* 各セクションにはディレクトリを割り当ててください。
* 画像にはPNGを使ってください。
* ディレクトリの名前は、小文字で次のタイトル例のように記述してください"getting-started"。
* 各ディレクトリには、01_slide.mdが１つ必要で、複数のセクションには後で分割することができます。

<!-- # Guides Directory -->
# Guideのディレクトリ

<!--
See the `instructor-setup.md` guide in the guides directory for
information on how to set up the lab environments for students to use
in the hands on portion of the course.
-->

ハンズオンやプロモーション講習会で生徒の実験環境を構築するには、
ガイドディレクトリの`instructor-setup.md` guideを見てください。


# Resources

http://daringfireball.net/projects/markdown/syntax
https://github.com/schacon/showoff

# Contributing

See CONTRIBUTING for information on how you can contribute changes to
these materials.

# License and Authors

See LICENSE for licensing of these materials and how you may use
them.

<!-- ## Authors: -->
## 著者:
* Joshua Timberman <joshua@opscode.com>
* Aaron Peterson <aaron@opscode.com>
* Stephen Nelson-Smith <stephen@atalanta-systems.com>

## 翻訳:
* Naotaka Jay Hott <j-hotta@cereationline.com>