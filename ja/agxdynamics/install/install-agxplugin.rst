
AGXDynamicsPluginのビルドとインストール
----------------------------------------

| AGXDynamicsPluginはChoreonoidのソースコードに同梱されております。
| Choreonoidのビルド前に行う :ref:`build-ubuntu-cmake` のcmakeオプションで
| 以下のオプションを **ON** にすることでビルドすることができます。

* **BUILD_AGX_DYNAMICS_PLUGIN**      : AGXDynamicsPlugin - AGX Dynamicsのシミュレーションプラグイン
* **BUILD_AGX_BODYEXTENSION_PLUGIN** : AGXBodyExtensionPlugin - 専用モデルプラグイン(ワイヤーなど)

| 以下にビルド、インストール方法の詳細を説明します。
| まず、choreonoidのソースディレクトリに移動し、ccmakeまでコマンドを実行します。

.. code-block:: txt

   cd choreonoid
   cmake .
   ccmake .

ccmakeで以下のオプションを有効にし、configure、generateを実行をします。

* BUILD_AGX_DYNAMICS_PLUGIN             ON
* BUILD_AGX_BODYEXTENSION_PLUGIN        ON

Cmake Errorがでていないことを確認し、以下のようにmake、make installを実行しビルド、インストールをします。

.. code-block:: txt

   make -j4
   make install   // インストール


.. note::

   AGXBodyExtensionPluginはAGXDynamicsPluginに依存しているため、BUILD_AGX_DYNAMICS_PLUGINがONにならないとccmakeで表示されません。
   一度BUILD_AGX_DYNAMICS_PLUGINをONにしてconfigureを実行してみてください。

.. note::

   ccmake configureを実行するとAGX DynamicsのパスAGX_DIRが自動的に設定されますが、設定されない場合には手動で設定をしてください。
   デフォルトのパスは /opt/Algoryx/AgX-<version>です。