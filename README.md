# Zygisk-Il2CppDumper

> 注意：代码中写死了从 0x100 和 0x104 找两个offset计算gm的文件大小
> 
> 在老旧的（gm未加密）版本中Phigros使用了 0x108，0x10C

Il2CppDumper with Zygisk, dump il2cpp data at runtime, can bypass protection, encryption and obfuscation.

写死了地址来导出一些初始化完成后会清零解密好的GM的游戏

自动提取GM地址：[gm_addr_extract](https://github.com/mokurin000/gm_addr_extract)

## Phigros TaptapCN Arm64

Version | Address
--------|--------
3.10.3  | 0x45975B8
3.10.2  | 0x45975B8
3.8.0   | 0x4597F38
3.6.0   | 0x459B7C0
3.5.2   | 0x458EA08
3.5.1   | 0x45936B8
3.5.0.1 | 0x458B2F8
3.4.3   | 0x457AF30
3.4.2   | 0x4578128
3.1.0   | 0x5015E88
2.5.1   | 0x4F18F90
2.5.0.1 | 0x4EBF660
2.1.0   | 0x24c4958
1.6.10  | 0x223E9E0

获取地址：

![image](https://github.com/000ylop/Zygisk-Il2CppDumper/assets/34085039/fea4354e-f42a-46f2-80dc-f57cf5210fe2)

中文说明请戳[这里](README.zh-CN.md)

## Credit

@[luoshuijs](https://github.com/luoshuijs)

## How to use
1. Install [Magisk](https://github.com/topjohnwu/Magisk) v24 or later and enable Zygisk
2. Build module
   - GitHub Actions
      1. Fork this repo
      2. Go to the **Actions** tab in your forked repo
      3. In the left sidebar, click the **Build** workflow.
      4. Above the list of workflow runs, select **Run workflow**
      5. Input the game package name and click **Run workflow**
      6. Wait for the action to complete and download the artifact
   - Android Studio
      1. Download the source code
      2. Edit `game.h`, modify `GamePackageName` to the game package name
      3. Use Android Studio to run the gradle task `:module:assembleRelease` to compile, the zip package will be generated in the `out` folder
3. Install module in Magisk
4. Start the game, `dump.cs` will be generated in the `/data/data/GamePackageName/files/` directory
