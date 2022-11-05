## Setup Fastlane

### ruby install

`$ brew install rbenv`

`$ rbenv install --list`

`$ rbenv local [version]` // .ruby-version ファイルが生成される

`$ rbenv install`


### bundle init

`$ rbenv exec bundle init` // Gemfile が作られる

`$ vi Gemfile` // Gemfile を編集 例: gem "fastlane", "~> 2.210.1"

`$ rbenv exec bundle config set --local CACHE_ALL true` // Cache を有効にする

`$ rbenv exec bundle config set --local PATH vendor/bundle` // Gemのインストール場所

`$ rbenv exec bundle`

`$ rbenv exec bundle package --all` // 手動で Cache する場合

###s fastlane init

`$ rbenv exec bundler exec fastlane init`

- Manual setup - manually setup your project to automate your tasks 普通はこの４番を選ぶ
- ここで Appfile と Fastfile が作られる
- Appfile は配布のためのADPのアカウント情報を入力するファイル
- Fastfile を編集する（下は例）

    ```
    default_platform(:ios)

    platform :ios do
      desc "Description of what the lane does"
      lane :[lane name] do
        build_app(
            scheme: "iOS",
            project: "[project name].xcodeproj",
            export_method: "enterprise",
            export_options: {
              "provisioningProfiles": {
                "[app bundle id]": "[provisioning profile name]"
              },
            },
            configuration: "[configuration name]",
            clean: true,
            output_directory: "build/",
            output_name: "[app name].ipa",
        )
      end
    end
    ```

`$ rbenv exec bundler exec fastlane [lane name]` // Localから実行する時
