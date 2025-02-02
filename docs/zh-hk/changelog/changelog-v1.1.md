# 版本更新記錄

# v1.1.32 - 2020-05-21

## 修復

- [#1734](https://github.com/hyperf/hyperf/pull/1734) 修復模型多態查詢，關聯關係為空時，也會查詢 SQL 的問題；
- [#1739](https://github.com/hyperf/hyperf/pull/1739) 修復 `hyperf/filesystem` 組件 OSS HOOK 位運算錯誤，導致 resource 判斷不準確的問題；
- [#1743](https://github.com/hyperf/hyperf/pull/1743) 修復 `grafana.json` 中錯誤的`refId` 字段值；
- [#1748](https://github.com/hyperf/hyperf/pull/1748) 修復 `hyperf/amqp` 組件在使用其他連接池時，對應的 `concurrent.limit` 配置不生效的問題；
- [#1750](https://github.com/hyperf/hyperf/pull/1750) 修復連接池組件，在連接關閉失敗時會導致計數有誤的問題；
- [#1754](https://github.com/hyperf/hyperf/pull/1754) 修復 BASE Server 服務，啓動提示沒有考慮 UDP 服務的情況；
- [#1764](https://github.com/hyperf/hyperf/pull/1764) 修復當時間值為 null 時，datatime 驗證器執行失敗的 BUG；
- [#1769](https://github.com/hyperf/hyperf/pull/1769) 修復 `hyperf/socketio-server` 組件中，客户端初始化斷開連接操作時會報 Notice 的錯誤的問題；

## 新增

- [#1724](https://github.com/hyperf/hyperf/pull/1724) 新增模型方法 `Model::orWhereHasMorph` ,`Model::whereDoesntHaveMorph` and `Model::orWhereDoesntHaveMorph`；
- [#1741](https://github.com/hyperf/hyperf/pull/1741) 新增 `Hyperf\Command\Command::choiceMultiple(): array` 方法，因為 `choice` 方法的返回類型為 `string，所以就算設置了 `$multiple` 參數也無法處理多個選擇的情況；
- [#1742](https://github.com/hyperf/hyperf/pull/1742) 新增模型 自定義類型轉換器 功能；
  - 新增 interface `Castable`, `CastsAttributes` 和 `CastsInboundAttributes`；
  - 新增方法 `Model\Builder::withCasts`；
  - 新增方法 `Model::loadMorph`, `Model::loadMorphCount` 和 `Model::syncAttributes`；

# v1.1.31 - 2020-05-14

## 新增

- [#1723](https://github.com/hyperf/hyperf/pull/1723) 異常處理器集成了 filp/whoops 。
- [#1730](https://github.com/hyperf/hyperf/pull/1730) 為命令 `gen:model` 可選項 `--refresh-fillable` 添加簡寫 `-R`。

## 修復

- [#1696](https://github.com/hyperf/hyperf/pull/1696) 修復方法 `Context::copy` 傳入字段 `keys` 後無法正常使用的 BUG。
- [#1708](https://github.com/hyperf/hyperf/pull/1708) [#1718](https://github.com/hyperf/hyperf/pull/1718) 修復 `hyperf/socketio-server` 組件內存溢出等 BUG。

## 優化

- [#1710](https://github.com/hyperf/hyperf/pull/1710) MAC 系統下不再使用 `cli_set_process_title` 方法設置進程名。

# v1.1.30 - 2020-05-07

## 新增

- [#1616](https://github.com/hyperf/hyperf/pull/1616) 新增 ORM 方法 `morphWith` 和 `whereHasMorph`。
- [#1651](https://github.com/hyperf/hyperf/pull/1651) 新增 `socket.io-server` 組件。
- [#1666](https://github.com/hyperf/hyperf/pull/1666) [#1669](https://github.com/hyperf/hyperf/pull/1669) 新增 AMQP RPC 客户端。

## 修復

- [#1682](https://github.com/hyperf/hyperf/pull/1682) 修復 `RpcPoolTransporter` 的連接池配置不生效的 BUG。
- [#1683](https://github.com/hyperf/hyperf/pull/1683) 修復 `RpcConnection` 連接失敗後，相同協程內無法正常重置連接的 BUG。

## 優化

- [#1670](https://github.com/hyperf/hyperf/pull/1670) 優化掉 `Cache 組件` 一條無意義的刪除指令。

# v1.1.28 - 2020-04-30

## 新增

- [#1645](https://github.com/hyperf/hyperf/pull/1645) 匿名函數路由支持參數注入。
- [#1647](https://github.com/hyperf/hyperf/pull/1647) 為 `model-cache` 組件添加 `RedisStringHandler`。
- [#1654](https://github.com/hyperf/hyperf/pull/1654) 新增 `RenderException` 統一捕獲 `view` 組件拋出的異常。

## 修復

- [#1639](https://github.com/hyperf/hyperf/pull/1639) 修復 `rpc-client` 會從 `consul` 中獲取到不健康節點的 BUG。
- [#1641](https://github.com/hyperf/hyperf/pull/1641) 修復 `rpc-client` 獲取到的結果為 `null` 時，會拋出 `RequestException` 的 BUG。
- [#1641](https://github.com/hyperf/hyperf/pull/1641) 修復 `rpc-server` 中 `jsonrpc-tcp-length-check` 協議，無法在 `consul` 中添加心跳檢查的 BUG。
- [#1650](https://github.com/hyperf/hyperf/pull/1650) 修復腳本 `describe:routes` 列表展示有誤的 BUG。
- [#1655](https://github.com/hyperf/hyperf/pull/1655) 修復 `MysqlProcessor::processColumns` 無法在 `MySQL Server 8.0` 版本中正常工作的 BUG。

## 優化

- [#1636](https://github.com/hyperf/hyperf/pull/1636) 優化 `co-phpunit` 腳本，當出現 `case` 驗證失敗後，協程也可以正常結束。


# v1.1.27 - 2020-04-23

## 新增

- [#1575](https://github.com/hyperf/hyperf/pull/1575) 為腳本 `gen:model` 生成的模型，自動添加 `relation` `scope` 和 `attributes` 的變量註釋。
- [#1586](https://github.com/hyperf/hyperf/pull/1586) 添加 `symfony/event-dispatcher` 組件小於 `4.3` 時的 `conflict` 配置。用於解決用户使用了 `4.3` 以下版本時，導致 `SymfonyDispatcher` 實現衝突的 BUG。
- [#1597](https://github.com/hyperf/hyperf/pull/1597) 為 `AMQP` 消費者，添加最大消費次數 `maxConsumption`。
- [#1603](https://github.com/hyperf/hyperf/pull/1603) 為 `WebSocket` 服務添加基於 `fd` 存儲的 `Context`。

## 修復

- [#1553](https://github.com/hyperf/hyperf/pull/1553) 修復 `jsonrpc` 服務，發佈了相同名字不同協議到 `consul` 後，客户端無法正常工作的 BUG。
- [#1589](https://github.com/hyperf/hyperf/pull/1589) 修復了文件鎖在協程下可能會造成死鎖的 BUG。
- [#1607](https://github.com/hyperf/hyperf/pull/1607) 修復了重寫後的 `go` 方法，返回值與 `swoole` 原生方法不符的 BUG。
- [#1624](https://github.com/hyperf/hyperf/pull/1624) 修復當路由 `Handler` 是匿名函數時，腳本 `describe:routes` 執行失敗的 BUG。

# v1.1.26 - 2020-04-16

## 新增

- [#1578](https://github.com/hyperf/hyperf/pull/1578) `UploadedFile` 支持 `getStream` 方法。

## 修復

- [#1563](https://github.com/hyperf/hyperf/pull/1563) 修復服務關停後，定時器的 `onOneServer` 配置不會被重置。
- [#1565](https://github.com/hyperf/hyperf/pull/1565) 當 `DB` 組件重連 `Mysql` 時，重置事務等級為 0。
- [#1572](https://github.com/hyperf/hyperf/pull/1572) 修復 `Hyperf\GrpcServer\CoreMiddleware` 中，自定義類的父類找不到時報錯的 BUG。
- [#1577](https://github.com/hyperf/hyperf/pull/1577) 修復 `describe:routes` 腳本 `server` 配置不生效的 BUG。
- [#1579](https://github.com/hyperf/hyperf/pull/1579) 修復 `migrate:refresh` 腳本 `step` 參數不為 `int` 時會報錯的 BUG。

## 變更

- [#1560](https://github.com/hyperf/hyperf/pull/1560) 修改 `hyperf/cache` 組件文件緩存引擎中 原生的文件操作為 `Filesystem`。
- [#1568](https://github.com/hyperf/hyperf/pull/1568) 修改 `hyperf/async-queue` 組件 `Redis` 引擎中的 `\Redis` 為 `RedisProxy`。

# v1.1.25 - 2020-04-09

## 修復

- [#1532](https://github.com/hyperf/hyperf/pull/1532) 修復 'Symfony\Component\EventDispatcher\EventDispatcherInterface' 在 --no-dev 條件下安裝會出現找不到接口的問題；


# v1.1.24 - 2020-04-09

## 新增

- [#1501](https://github.com/hyperf/hyperf/pull/1501) 添加 `Symfony` 命令行事件觸發器，使之可以與 `hyperf/event` 組件結合使用；
- [#1502](https://github.com/hyperf/hyperf/pull/1502) 為註解 `Hyperf\AsyncQueue\Annotation\AsyncQueueMessage` 添加 `maxAttempts` 參數，用於控制消息失敗時重複消費的次數；
- [#1510](https://github.com/hyperf/hyperf/pull/1510) 添加 `Hyperf/Utils/CoordinatorManager`，用於提供更優雅的啓動和停止服務，服務啓動前不響應請求，服務停止前，保證某些循環邏輯能夠正常結束；
- [#1517](https://github.com/hyperf/hyperf/pull/1517) 為依賴注入容器的懶加載功能添加了對接口繼承和抽象方法繼承的支持；
- [#1529](https://github.com/hyperf/hyperf/pull/1529) 處理 `response cookies` 中的 `SameSite` 屬性；

## 修復

- [#1494](https://github.com/hyperf/hyperf/pull/1494) 修復單獨使用 `Redis` 組件時，註釋 `@mixin` 會被當成註解的 BUG；
- [#1499](https://github.com/hyperf/hyperf/pull/1499) 修復引入 `hyperf/translation` 組件後，`hyperf/constants` 組件的動態參數不生效的 BUG；
- [#1504](https://github.com/hyperf/hyperf/pull/1504) 修復 `RPC` 代理客户端無法正常處理返回值為 `nullable` 類型的方法；
- [#1507](https://github.com/hyperf/hyperf/pull/1507) 修復 `hyperf/consul` 組件的 `catalog` 註冊方法調用會失敗的 BUG；

# v1.1.23 - 2020-04-02

## 新增

- [#1467](https://github.com/hyperf/hyperf/pull/1467) 為 `filesystem` 組件添加默認配置；
- [#1469](https://github.com/hyperf/hyperf/pull/1469) 為 `Hyperf/Guzzle/HandlerStackFactory` 添加 `getHandler()` 方法，並儘可能的使用 `make()` 創建 `handler`；
- [#1480](https://github.com/hyperf/hyperf/pull/1480) RPC client 現在會自動代理父接口的方法定義；

## 變更

- [#1481](https://github.com/hyperf/hyperf/pull/1481) 異步隊列創建消息時，使用 `make` 方法創建；

## 修復

- [#1471](https://github.com/hyperf/hyperf/pull/1471) 修復 `NSQ` 組件，數據量超過 `max-output-buffer-size` 接收數據失敗的 `BUG`；
- [#1472](https://github.com/hyperf/hyperf/pull/1472) 修復 `NSQ` 組件，在消費者中發佈消息時，會導致消費者無法正常消費的 `BUG`；
- [#1474](https://github.com/hyperf/hyperf/pull/1474) 修復 `NSQ` 組件，`requeue` 消息時，消費者會意外重啓的 `BUG`；
- [#1477](https://github.com/hyperf/hyperf/pull/1477) 修復使用 `Hyperf\Testing\Client::flushContext` 時，會引發 `Fixed Invalid argument supplied` 異常的 `BUG`；

# v1.1.22 - 2020-03-26

## 新增

- [#1440](https://github.com/hyperf/hyperf/pull/1440) 為 NSQ 的每個連接新增 `enable` 配置項來控制連接下的所有消費者的自啓功能；
- [#1451](https://github.com/hyperf/hyperf/pull/1451) 新增 Filesystem 組件；
- [#1459](https://github.com/hyperf/hyperf/pull/1459) 模型 Collection 新增 macroable 支持；
- [#1463](https://github.com/hyperf/hyperf/pull/1463) 為 Guzzle Handler 增加 `on_stats` 選項的功能支持；

## 變更

- [#1452](https://github.com/hyperf/hyperf/pull/1452) 在注入 Redis 客户端時，推薦使用 `\Hyperf\Redis\Redis` 來替代 `\Redis`，原因在 [#938](https://github.com/hyperf/hyperf/issues/938)；

## 修復

- [#1445](https://github.com/hyperf/hyperf/pull/1445) 修復命令 `describe:routes` 缺失了帶參數的路由；
- [#1449](https://github.com/hyperf/hyperf/pull/1449) 修復了高基數請求路徑的內存溢出的問題；
- [#1454](https://github.com/hyperf/hyperf/pull/1454) 修復 Collection 的 `flatten()` 方法因為 `INF` 參數值為 `float` 類型導致無法使用的問題；
- [#1458](https://github.com/hyperf/hyperf/pull/1458) 修復了 Guzzle 不支持 Elasticsearch 版本大於 7.0 的問題；

# v1.1.21 - 2020-03-19

## 新增

- [#1393](https://github.com/hyperf/hyperf/pull/1393) 為 `Hyperf\HttpMessage\Stream\SwooleStream` 實現更多的方法；
- [#1419](https://github.com/hyperf/hyperf/pull/1419) 允許 ConfigFetcher 通過一個協程啓動而無需額外啓動一個進程；
- [#1424](https://github.com/hyperf/hyperf/pull/1424) 允許用户通過配置文件的形式修改 `session_name` 配置；
- [#1435](https://github.com/hyperf/hyperf/pull/1435) 為模型緩存增加 `use_default_value` 屬性來自動修正緩存數據與數據庫數據之間的差異；
- [#1436](https://github.com/hyperf/hyperf/pull/1436) 為 NSQ 消費者增加 `isEnable()` 方法來控制消費者進程是否啓用自啓功能；

# v1.1.20 - 2020-03-12

## 新增

- [#1402](https://github.com/hyperf/hyperf/pull/1402) 增加 `Hyperf\DbConnection\Annotation\Transactional` 註解來自動開啓一個事務；
- [#1412](https://github.com/hyperf/hyperf/pull/1412) 增加 `Hyperf\View\RenderInterface::getContents()` 方法來直接獲取 View Render 的渲染內容；
- [#1416](https://github.com/hyperf/hyperf/pull/1416) 增加 Swoole 事件常量 `ON_WORKER_ERROR`.

## 修復

- [#1405](https://github.com/hyperf/hyperf/pull/1405) 修復當模型存在 `hidden` 屬性時，模型緩存功能緩存的字段數據不正確的問題；
- [#1410](https://github.com/hyperf/hyperf/pull/1410) 修復 Tracer 無法追蹤由 `Hyperf\Redis\RedisFactory` 創建的連接的調用鏈；
- [#1415](https://github.com/hyperf/hyperf/pull/1415) 修復阿里 ACM 客户端在當 `SecurityToken` Header 為空時 sts token 會解密失敗的問題；


# v1.1.19 - 2020-03-05

## 新增

- [#1339](https://github.com/hyperf/hyperf/pull/1339) [#1394](https://github.com/hyperf/hyperf/pull/1394) 新增 `describe:routes` 命令來顯示路由的細節信息；
- [#1354](https://github.com/hyperf/hyperf/pull/1354) 為  `config-aliyun-acm` 組件新增 ecs ram authorization；
- [#1362](https://github.com/hyperf/hyperf/pull/1362) 為 `Hyperf\Pool\SimplePool\PoolFactory` 增加 `getPoolNames()` 來獲取連接池的名稱；
- [#1371](https://github.com/hyperf/hyperf/pull/1371) 新增 `Hyperf\DB\DB::connection()` 方法來指定要使用的連接；
- [#1384](https://github.com/hyperf/hyperf/pull/1384) 為 `gen:model` 命令新增  `property-case` 選項來設定成員屬性的命名風格；

## 修復

- [#1386](https://github.com/hyperf/hyperf/pull/1386) 修復異步消息投遞註解當用在存在可變參數的方法上失效的問題；

# v1.1.18 - 2020-02-27

## 新增

- [#1305](https://github.com/hyperf/hyperf/pull/1305) 為 `hyperf\metric` 組件添加預製的 `Grafana` 面板；
- [#1328](https://github.com/hyperf/hyperf/pull/1328) 添加 `ModelRewriteInheritanceVisitor` 來重寫 model 類繼承的 `gen:model` 命令；
- [#1331](https://github.com/hyperf/hyperf/pull/1331) 添加 `Hyperf\LoadBalancer\LoadBalancerInterface::getNodes()`；
- [#1335](https://github.com/hyperf/hyperf/pull/1335) 為 `command` 添加 `AfterExecute` 事件；
- [#1361](https://github.com/hyperf/hyperf/pull/1361) logger 組件添加 `processors` 配置；

## 修復

- [#1330](https://github.com/hyperf/hyperf/pull/1330) 修復當使用 `(new Parallel())->add($callback, $key)` 並且參數 `$key` 並非 string 類型, 返回結果將會從 0 開始排序 `$key`；
- [#1338](https://github.com/hyperf/hyperf/pull/1338) 修復當從 server 設置自己的設置時, 主 server 的配置不生效的 bug；
- [#1344](https://github.com/hyperf/hyperf/pull/1344) 修復隊列在沒有設置最大消息數時每次都需要校驗長度的 bug；

## 變更

- [#1324](https://github.com/hyperf/hyperf/pull/1324) [hyperf/async-queue](https://github.com/hyperf/async-queue) 組件不再提供默認啓用 `Hyperf\AsyncQueue\Listener\QueueLengthListener`；

## 優化

- [#1305](https://github.com/hyperf/hyperf/pull/1305) 優化 `hyperf\metric` 中的邊界條件；
- [#1322](https://github.com/hyperf/hyperf/pull/1322) HTTP Server 自動處理 HEAD 請求並且不會在 HEAD 請求時返回 Response body；

## 刪除

- [#1303](https://github.com/hyperf/hyperf/pull/1303) 刪除 `Hyperf\RpcServer\Router\Router` 中無用的 `$httpMethod`；

# v1.1.17 - 2020-01-24

## 新增

- [#1220](https://github.com/hyperf/hyperf/pull/1220) 為 Apollo 組件增加 BootProcessListener 來實現在服務啓動時從 Apollo 拉取配置的功能；
- [#1292](https://github.com/hyperf/hyperf/pull/1292) 為 `Hyperf\Database\Schema\Blueprint::foreign()` 方法的返回類型增加了 `Hyperf\Database\Schema\ForeignKeyDefinition` 類型；
- [#1313](https://github.com/hyperf/hyperf/pull/1313) 為 `hyperf\crontab` 組件增加了 Command 模式支持；
- [#1321](https://github.com/hyperf/hyperf/pull/1321) 增加 [hyperf/nsq](https://github.com/hyperf/nsq) 組件，[NSQ](https://nsq.io) 是一個實時的分佈式消息平台；

## 修復

- [#1291](https://github.com/hyperf/hyperf/pull/1291) 修復 [hyperf/super-globals](https://github.com/hyperf/super-globals) 組件的 `$_SERVER` 存在小寫鍵值與 PHP-FPM 不統一的問題；
- [#1308](https://github.com/hyperf/hyperf/pull/1308) 修復 [hyperf/validation](https://github.com/hyperf/validation) 組件缺失的一些翻譯內容, 包括 gt, gte, ipv4, ipv6, lt, lte, mimetypes, not_regex, starts_with, uuid；
- [#1310](https://github.com/hyperf/hyperf/pull/1310) 修復服務註冊在當服務同名不同協議的情況下會被覆蓋的問題；
- [#1315](https://github.com/hyperf/hyperf/pull/1315) 修復 `Hyperf\AsyncQueue\Process\ConsumerProcess` 類缺失的 $config 變量；

# v1.1.16 - 2020-01-16

## 新增

- [#1263](https://github.com/hyperf/hyperf/pull/1263) 為 async-queue 組件增加 `QueueLength` 事件；
- [#1276](https://github.com/hyperf/hyperf/pull/1276) 為 Consul 客户端增加 ACL token 支持；
- [#1277](https://github.com/hyperf/hyperf/pull/1277) 為 [hyperf/metric](https://github.com/hyperf/metric) 組件增加 NoOp 驅動，用來臨時關閉 metric 功能；

## 修復

- [#1262](https://github.com/hyperf/hyperf/pull/1262) 修復 keepaliveIO 功能下 socket 會被消耗光的問題；
- [#1266](https://github.com/hyperf/hyperf/pull/1266) 修復當自定義進程存在 Timer 的情況下會無法重啓的問題；
- [#1272](https://github.com/hyperf/hyperf/pull/1272) 修復 JSONRPC 下當 Request ID 為 null 時檢查會失敗的問題；

## 優化

- [#1273](https://github.com/hyperf/hyperf/pull/1273) 優化 gRPC 客户端：
  - 優化使 gRPC 客户端在當連接與 Server 斷開時會自動重連；
  - 優化使當 gRPC 客户端被垃圾回收時，已建立的連接會自動關閉；
  - 修復關閉了的客户端依舊會持有 HTTP2 連接的問題；
  - 修復 gRPC 客户端的 channel pool 可能會存在非空 channel 的問題；
  - 優化使 gRPC 客户端會自動初始化，所以現在可以在構造函數和容器注入下使用；

## 刪除

- [#1286](https://github.com/hyperf/hyperf/pull/1286) 從 require-dev 中移除 [phpstan/phpstan](https://github.com/phpstan/phpstan) 包的依賴。

# v1.1.15 - 2020-01-10

## 修復

- [#1258](https://github.com/hyperf/hyperf/pull/1258) 修復 AMQP 發送心跳失敗，會導致子進程 Socket 通信不可用的問題；
- [#1260](https://github.com/hyperf/hyperf/pull/1260) 修復 JSONRPC 在同一協程內，連接會混淆複用的問題；

# v1.1.14 - 2020-01-10

## 新增

- [#1166](https://github.com/hyperf/hyperf/pull/1166) 為 AMQP 增加 KeepaliveIO 功能；
- [#1208](https://github.com/hyperf/hyperf/pull/1208) 為 JSON-RPC 的響應增加了 `error.data.code` 值來傳遞 Exception Code；
- [#1208](https://github.com/hyperf/hyperf/pull/1208) 為 `Hyperf\Rpc\Contract\TransporterInterface` 增加了 `recv` 方法；
- [#1215](https://github.com/hyperf/hyperf/pull/1215) 新增 [hyperf/super-globals](https://github.com/hyperf/super-globals) 組件，用來適配一些不支持 PSR-7 的第三方包；
- [#1219](https://github.com/hyperf/hyperf/pull/1219) 為 AMQP 消費者增加 `enable` 屬性，通過該屬性來控制該消費者是否跟隨 Server 一同啓動；

## 修復

- [#1208](https://github.com/hyperf/hyperf/pull/1208) 修復 Exception 和 error 在 JSON-RPC TCP Server 下無法被正確處理的問題；
- [#1208](https://github.com/hyperf/hyperf/pull/1208) 修復 JSON-RPC 沒有檢查 Request ID 和 Response ID 是否一致的問題；
- [#1223](https://github.com/hyperf/hyperf/pull/1223) 修復 ConfigProvider 掃描器不會掃描 composer.json 內 require-dev 的配置；
- [#1254](https://github.com/hyperf/hyperf/pull/1254) 修復執行 `init-proxy.sh` 命令在某些環境如 Alpine 下會報 bash 不存在的問題；

## 優化

- [#1208](https://github.com/hyperf/hyperf/pull/1208) 優化了 JSON-RPC 組件的部分邏輯；
- [#1174](https://github.com/hyperf/hyperf/pull/1174) 調整了 `Hyperf\Utils\Parallel` 在輸出異常時的格式，現在會一同打印 Trace 信息；
- [#1224](https://github.com/hyperf/hyperf/pull/1224) 允許 Aliyun ACM 配置中心的配置獲取進程解析 UTF-8 字符，同時在 Worker 啓動後會自動獲取一次配置，以及拉取的配置現在會傳遞到自定義進程了；
- [#1235](https://github.com/hyperf/hyperf/pull/1235) 在 AMQP 生產者執行 declare 後釋放對應的連接；

## 修改

- [#1227](https://github.com/hyperf/hyperf/pull/1227) 升級 `jcchavezs/zipkin-php-opentracing` 依賴至 0.1.4 版本；

# v1.1.13 - 2020-01-03

## 新增

- [#1137](https://github.com/hyperf/hyperf/pull/1137) `constants` 組件增加國際化支持；
- [#1165](https://github.com/hyperf/hyperf/pull/1165) `Hyperf\HttpServer\Contract\RequestInterface` 新增 `route` 方法；
- [#1195](https://github.com/hyperf/hyperf/pull/1195) 註解 `Cacheable` 和 `CachePut` 增加最大超時時間偏移量配置；
- [#1204](https://github.com/hyperf/hyperf/pull/1204) `database` 組件增加了 `insertOrIgnore` 方法；
- [#1216](https://github.com/hyperf/hyperf/pull/1216) `RenderInterface::render()` 方法的 `$data` 參數，添加了默認值；
- [#1221](https://github.com/hyperf/hyperf/pull/1221) `swoole-tracker` 組件添加了 `traceId` 和 `spanId`；

## 修復

- [#1175](https://github.com/hyperf/hyperf/pull/1175) 修復 `Hyperf\Utils\Collection::random` 當傳入 `null` 時，無法正常工作的 `BUG`；
- [#1199](https://github.com/hyperf/hyperf/pull/1199) 修復使用 `Task` 註解時，參數無法使用動態變量的 `BUG`；
- [#1200](https://github.com/hyperf/hyperf/pull/1200) 修復 `metric` 組件，請求路徑會攜帶參數的 `BUG`；
- [#1210](https://github.com/hyperf/hyperf/pull/1210) 修復驗證器規則 `size` 無法作用於 `integer` 的 `BUG`；

## 優化

- [#1211](https://github.com/hyperf/hyperf/pull/1211) 自動將項目名轉化為 `prometheus` 的規範命名；

## 修改

- [#1217](https://github.com/hyperf/hyperf/pull/1217) 將 `zendframework/zend-mime` 替換為 `laminas/laminas-mine`；

# v1.1.12 - 2019-12-26

## 新增

- [#1177](https://github.com/hyperf/hyperf/pull/1177) 為 `jsonrpc` 組件增加了新的協議 `jsonrpc-tcp-length-check`，並對部分代碼進行了優化；

## 修復

- [#1175](https://github.com/hyperf/hyperf/pull/1175) 修復 `Hyperf\Utils\Collection::random` 方法不支持傳入 `null`；
- [#1178](https://github.com/hyperf/hyperf/pull/1178) 修復 `Hyperf\Database\Query\Builder::chunkById` 方法不支持元素是 `array` 的情況；
- [#1189](https://github.com/hyperf/hyperf/pull/1189) 修復 `Hyperf\Utils\Collection::operatorForWhere` 方法，`operator` 只能傳入 `string` 的 BUG；

## 優化

- [#1186](https://github.com/hyperf/hyperf/pull/1186) 日誌配置中，只填寫 `formatter.class` 的情況下，可以使用默認的 `formatter.constructor` 配置；

# v1.1.11 - 2019-12-19

## 新增

- [#849](https://github.com/hyperf/hyperf/pull/849) 為 hyperf/tracer 組件增加 span tag 配置功能；

## 修復

- [#1142](https://github.com/hyperf/hyperf/pull/1142) 修復 `Register::resolveConnection` 會返回 null 的問題；
- [#1144](https://github.com/hyperf/hyperf/pull/1144) 修復配置文件形式下服務限流會失效的問題；
- [#1145](https://github.com/hyperf/hyperf/pull/1145) 修復 `CoroutineMemoryDriver::delKey` 方法的返回值錯誤的問題；
- [#1153](https://github.com/hyperf/hyperf/pull/1153) 修復驗證器的 `alpha_num` 規則無法按預期運行的問題；

# v1.1.10 - 2019-12-12

## 修復

- [#1104](https://github.com/hyperf/hyperf/pull/1104) 修復了 Guzzle 客户端的重試中間件的狀態碼識別範圍為 2xx；
- [#1105](https://github.com/hyperf/hyperf/pull/1105) 修復了 Retry 組件在重試嘗試前不還原管道堆棧的問題；
- [#1106](https://github.com/hyperf/hyperf/pull/1106) 修復了數據庫在開啓 `sticky` 模式時連接回歸連接池時沒有重置狀態的問題；
- [#1119](https://github.com/hyperf/hyperf/pull/1119) 修復 TCP 協議下的 JSONRPC Server 在解析 JSON 失敗時無法正確的返回預期的 Error Response 的問題；
- [#1124](https://github.com/hyperf/hyperf/pull/1124) 修復 Session 中間件在儲存當前的 URL 時，當 URL 以 `/` 結尾時會忽略斜槓的問題；

## 變更

- [#1108](https://github.com/hyperf/hyperf/pull/1108) 重命名 `Hyperf\Tracer\Middleware\TraceMiddeware` 為 `Hyperf\Tracer\Middleware\TraceMiddleware`；
- [#1108](https://github.com/hyperf/hyperf/pull/1111) 升級 `Hyperf\ServiceGovernance\Listener\ServiceRegisterListener` 類的成員屬性和方法的等級為 `protected`，以便更好的重寫相關方法；

# v1.1.9 - 2019-12-05

## 新增

- [#948](https://github.com/hyperf/hyperf/pull/948) 為 DI Container 增加懶加載功能；
- [#1044](https://github.com/hyperf/hyperf/pull/1044) 為 AMQP Consumer 增加 `basic_qos` 配置；
- [#1056](https://github.com/hyperf/hyperf/pull/1056) [#1081](https://github.com/hyperf/hyperf/pull/1081) DI Container 增加 `define()` 和 `set()` 方法，同時增加 `Hyperf\Contract\ContainerInterface`；
- [#1059](https://github.com/hyperf/hyperf/pull/1059) `job.stub` 模板增加構造函數；
- [#1084](https://github.com/hyperf/hyperf/pull/1084) 支持 PHP 7.4，TrvisCI 增加 PHP 7.4 運行支持；

## 修復

- [#1007](https://github.com/hyperf/hyperf/pull/1007) 修復 `vendor:: publish` 的命令返回值；
- [#1049](https://github.com/hyperf/hyperf/pull/1049) 修復 `Hyperf\Cache\Driver\RedisDriver::clear` 會有可能刪除所有緩存失敗的問題；
- [#1055](https://github.com/hyperf/hyperf/pull/1055) 修復 Image 驗證時後綴大小寫的問題；
- [#1085](https://github.com/hyperf/hyperf/pull/1085) [#1091](https://github.com/hyperf/hyperf/pull/1091) Fixed `@Retry` 註解使用時會找不到容器的問題；

# v1.1.8 - 2019-11-28

## 新增

- [#965](https://github.com/hyperf/hyperf/pull/965) 新增 Redis Lua 模塊，用於管理 Lua 腳本；
- [#1023](https://github.com/hyperf/hyperf/pull/1023) hyperf/metric 組件的 Prometheus 驅動新增 CUSTOM_MODE 模式；

## 修復

- [#1013](https://github.com/hyperf/hyperf/pull/1013) 修復 JsonRpcPoolTransporter 配置合併失敗的問題；
- [#1006](https://github.com/hyperf/hyperf/pull/1006) 修復 `gen:model` 命令生成的屬性的順序；

## 變更

- [#1021](https://github.com/hyperf/hyperf/pull/1012) WebSocket 客户端新增默認端口支持，根據協議默認為 80 和 443；
- [#1034](https://github.com/hyperf/hyperf/pull/1034) 去掉了 `Hyperf\Amqp\Builder\Builder` 的 `arguments` 參數的 array 類型限制，允許接受其他類型如 AmqpTable；

## 優化

- [#1014](https://github.com/hyperf/hyperf/pull/1014) 優化 `Command::execute` 的返回值類型；
- [#1022](https://github.com/hyperf/hyperf/pull/1022) 提供更清晰友好的連接池報錯信息；
- [#1039](https://github.com/hyperf/hyperf/pull/1039) 在 CoreMiddleware 中自動設置最新的 ServerRequest 對象到 Context；

# v1.1.7 - 2019-11-21

## 新增

- [#860](https://github.com/hyperf/hyperf/pull/860) 新增 [hyperf/retry](https://github.com/hyperf/retry) 組件；
- [#952](https://github.com/hyperf/hyperf/pull/952) 新增 ThinkTemplate 視圖引擎支持；
- [#973](https://github.com/hyperf/hyperf/pull/973) 新增 JSON RPC 在 TCP 協議下的連接池支持，通過 `Hyperf\JsonRpc\JsonRpcPoolTransporter` 來使用連接池版本；
- [#976](https://github.com/hyperf/hyperf/pull/976) 為 `hyperf/amqp` 組件新增  `close_on_destruct` 選項參數，用來控制代碼在執行析構函數時是否主動去關閉連接；

## 變更

- [#944](https://github.com/hyperf/hyperf/pull/944) 將組件內所有使用 `@Listener` 和 `@Process` 註解來註冊的改成通過 `ConfigProvider`來註冊；
- [#977](https://github.com/hyperf/hyperf/pull/977) 調整 `init-proxy.sh` 命令的行為，改成只刪除 `runtime/container` 目錄；

## 修復

- [#955](https://github.com/hyperf/hyperf/pull/955) 修復 `hyperf/db` 組件的 `port` 和 `charset` 參數無效的問題；
- [#956](https://github.com/hyperf/hyperf/pull/956) 修復模型緩存中使用到`RedisHandler::incr` 在集羣模式下會失敗的問題；
- [#966](https://github.com/hyperf/hyperf/pull/966) 修復當在非 Worker 進程環境下使用分頁器會報錯的問題；
- [#968](https://github.com/hyperf/hyperf/pull/968) 修復當 `classes` 和 `annotations` 兩種 Aspect 切入模式同時存在於一個類時，其中一個可能會失效的問題；
- [#980](https://github.com/hyperf/hyperf/pull/980) 修復 Session 組件內 `migrate`, `save` 核 `has` 方法無法使用的問題；
- [#982](https://github.com/hyperf/hyperf/pull/982) 修復 `Hyperf\GrpcClient\GrpcClient::yield` 在獲取 Channel Pool 時沒有通過正確的獲取方式去獲取的問題；
- [#987](https://github.com/hyperf/hyperf/pull/987) 修復通過 `gen:command` 命令生成的命令類缺少調用 `parent::configure()` 方法的問題；

## 優化

- [#991](https://github.com/hyperf/hyperf/pull/991) 優化 `Hyperf\DbConnection\ConnectionResolver::connection`的異常情況處理；

# v1.1.6 - 2019-11-14

## 新增

- [#827](https://github.com/hyperf/hyperf/pull/827) 新增了極簡的高性能的 DB 組件；
- [#905](https://github.com/hyperf/hyperf/pull/905) 視圖組件增加了 `twig` 模板引擎；
- [#911](https://github.com/hyperf/hyperf/pull/911) 定時任務支持多實例情況下，只運行單一實例的定時任務；
- [#913](https://github.com/hyperf/hyperf/pull/913) 增加監聽器 `Hyperf\ExceptionHandler\Listener\ErrorExceptionHandler`；
- [#921](https://github.com/hyperf/hyperf/pull/921) 新增 `Session` 組件；
- [#931](https://github.com/hyperf/hyperf/pull/931) 阿波羅配置中心增加 `strict_mode`，自動將配置轉化成對應數據類型；
- [#933](https://github.com/hyperf/hyperf/pull/933) 視圖組件增加了 `plates` 模板引擎；
- [#937](https://github.com/hyperf/hyperf/pull/937) Nats 組件添加消費者消費和訂閲事件；
- [#941](https://github.com/hyperf/hyperf/pull/941) 新增 `Zookeeper` 配置中心；

## 變更

- [#934](https://github.com/hyperf/hyperf/pull/934) 修改 `WaitGroup` 繼承 `\Swoole\Coroutine\WaitGroup`；

## 修復

- [#897](https://github.com/hyperf/hyperf/pull/897) 修復 `Nats` 消費者，`pool` 配置無效的 BUG；
- [#901](https://github.com/hyperf/hyperf/pull/901) 修復 `GraphQL` 組件，`Factory` 註解無法正常使用的 BUG；
- [#903](https://github.com/hyperf/hyperf/pull/903) 修復添加 `hyperf/rpc-client` 依賴後，`init-proxy` 腳本無法正常停止的 BUG；
- [#904](https://github.com/hyperf/hyperf/pull/904) 修復監聽器監聽 `Hyperf\Framework\Event\BeforeMainServerStart` 事件時，無法使用 `IO` 操作的 BUG；
- [#906](https://github.com/hyperf/hyperf/pull/906) 修復 `Hyperf\HttpMessage\Server\Request` 端口獲取有誤的 BUG；
- [#907](https://github.com/hyperf/hyperf/pull/907) 修復 `Nats` 組件 `requestSync` 方法，超時時間不準確的 BUG；
- [#909](https://github.com/hyperf/hyperf/pull/909) 修復 `Parallel` 內邏輯拋錯後，無法正常停止的 BUG；
- [#925](https://github.com/hyperf/hyperf/pull/925) 修復因 `Socket` 無法正常建立，導致進程頻繁重啓的 BUG；
- [#932](https://github.com/hyperf/hyperf/pull/932) 修復 `Translator::setLocale` 在協程環境下，數據混淆的 BUG；
- [#940](https://github.com/hyperf/hyperf/pull/940) 修復 `WebSocketClient::push` 方法 `finish` 參數類型錯誤；

## 優化

- [#907](https://github.com/hyperf/hyperf/pull/907) 優化 `Nats` 消費者頻繁重啓；
- [#928](https://github.com/hyperf/hyperf/pull/928) `Hyperf\ModelCache\Cacheable::query` 批量修改數據時，可以刪除對應緩存；
- [#936](https://github.com/hyperf/hyperf/pull/936) 優化調用模型緩存 `increment` 時，可能因併發情況導致的數據有錯；

# v1.1.5 - 2019-11-07

## 新增

- [#812](https://github.com/hyperf/hyperf/pull/812) 新增計劃任務在集羣下僅執行一次的支持；
- [#820](https://github.com/hyperf/hyperf/pull/820) 新增 hyperf/nats 組件；
- [#832](https://github.com/hyperf/hyperf/pull/832) 新增 `Hyperf\Utils\Codec\Json`；
- [#833](https://github.com/hyperf/hyperf/pull/833) 新增 `Hyperf\Utils\Backoff`；
- [#852](https://github.com/hyperf/hyperf/pull/852) 為 `Hyperf\Utils\Parallel` 新增 `clear()` 方法來清理所有已添加的回調；
- [#854](https://github.com/hyperf/hyperf/pull/854) 新增 `Hyperf\GraphQL\GraphQLMiddleware` 用於解析 GraphQL 請求；
- [#859](https://github.com/hyperf/hyperf/pull/859) 新增 Consul 集羣的支持，現在可以從 Consul 集羣中拉取服務提供者的節點信息；
- [#873](https://github.com/hyperf/hyperf/pull/873) 新增 Redis 集羣的客户端支持；

## 修復

- [#831](https://github.com/hyperf/hyperf/pull/831) 修復 Redis 客户端連接在 Redis Server 重啓後不會自動重連的問題；
- [#835](https://github.com/hyperf/hyperf/pull/835) 修復 `Request::inputs` 方法的默認值參數與預期效果不一致的問題；
- [#841](https://github.com/hyperf/hyperf/pull/841) 修復數據庫遷移在多數據庫的情況下連接無效的問題；
- [#844](https://github.com/hyperf/hyperf/pull/844) 修復 Composer 閲讀器不支持根命名空間的用法的問題；
- [#846](https://github.com/hyperf/hyperf/pull/846) 修復 Redis 客户端的 `scan`, `hScan`, `zScan`, `sScan` 無法使用的問題；
- [#850](https://github.com/hyperf/hyperf/pull/850) 修復 Logger group 在 name 一樣時不生效的問題；

## 優化

- [#832](https://github.com/hyperf/hyperf/pull/832) 優化了 Response 對象在轉 JSON 格式時的異常處理邏輯；
- [#840](https://github.com/hyperf/hyperf/pull/840) 使用 `\Swoole\Timer::*` 來替代 `swoole_timer_*` 函數；
- [#859](https://github.com/hyperf/hyperf/pull/859) 優化了 RPC 客户端去 Consul 獲取健康的節點信息的邏輯；

# v1.1.4 - 2019-10-31

## 新增

- [#778](https://github.com/hyperf/hyperf/pull/778) `Hyperf\Testing\Client` 新增 `PUT` 和 `DELETE`方法；
- [#784](https://github.com/hyperf/hyperf/pull/784) 新增服務監控組件；
- [#795](https://github.com/hyperf/hyperf/pull/795) `AbstractProcess` 增加 `restartInterval` 參數，允許子進程異常或正常退出後，延遲重啓；
- [#804](https://github.com/hyperf/hyperf/pull/804) `Command` 增加事件 `BeforeHandle` `AfterHandle` 和 `FailToHandle`；

## 變更

- [#793](https://github.com/hyperf/hyperf/pull/793) `Pool::getConnectionsInChannel` 方法由 `protected` 改為 `public`.
- [#811](https://github.com/hyperf/hyperf/pull/811) 命令 `di:init-proxy` 不再主動清理代理緩存，如果想清理緩存請使用命令 `vendor/bin/init-proxy.sh`；

## 修復

- [#779](https://github.com/hyperf/hyperf/pull/779) 修復 `JPG` 文件驗證不通過的問題；
- [#787](https://github.com/hyperf/hyperf/pull/787) 修復 `db:seed` 參數 `--class` 多餘，導致報錯的問題；
- [#795](https://github.com/hyperf/hyperf/pull/795) 修復自定義進程在異常拋出後，無法正常重啓的 BUG；
- [#796](https://github.com/hyperf/hyperf/pull/796) 修復 `etcd` 配置中心 `enable` 即時設為 `false`，在項目啓動時，依然會拉取配置的 BUG；

## 優化

- [#781](https://github.com/hyperf/hyperf/pull/781) 可以根據國際化組件配置發佈驗證器語言包到規定位置；
- [#796](https://github.com/hyperf/hyperf/pull/796) 優化 `ETCD` 客户端，不會多次創建 `HandlerStack`；
- [#797](https://github.com/hyperf/hyperf/pull/797) 優化子進程重啓

# v1.1.3 - 2019-10-24

## 新增

- [#745](https://github.com/hyperf/hyperf/pull/745) 為 `gen:model` 命令增加 `with-comments` 選項，以標記是否生成字段註釋；
- [#747](https://github.com/hyperf/hyperf/pull/747) 為 AMQP 消費者增加 `AfterConsume`, `BeforeConsume`, `FailToConsume` 事件；
- [#762](https://github.com/hyperf/hyperf/pull/762) 為 Parallel 特性增加協程控制功能；

## 變更

- [#767](https://github.com/hyperf/hyperf/pull/767) 重命名 `AbstractProcess` 的 `running` 屬性名為 `listening`；

## 修復

- [#741](https://github.com/hyperf/hyperf/pull/741) 修復執行 `db:seed` 命令缺少文件名報錯的問題；
- [#748](https://github.com/hyperf/hyperf/pull/748) 修復 `SymfonyNormalizer` 不處理 `array` 類型數據的問題；
- [#769](https://github.com/hyperf/hyperf/pull/769) 修復當 JSON RPC 響應的結果的 result 和 error 屬性為 null 時會拋出一個無效請求的問題；

# v1.1.2 - 2019-10-17

## 新增

- [#722](https://github.com/hyperf-cloud/hyperf/pull/722) 為 AMQP Consumer 新增 `concurrent.limit` 配置來對協程消費進行速率限制；

## 變更

- [#678](https://github.com/hyperf-cloud/hyperf/pull/678) 為 `gen:model` 命令增加 `ignore-tables` 參數，同時默認屏蔽 `migrations` 表，即 `migrations` 表對應的模型在執行 `gen:model` 命令時不會生成；

## 修復

- [#694](https://github.com/hyperf-cloud/hyperf/pull/694) 修復 `Hyperf\Validation\Request\FormRequest` 的 `validationData` 方法不包含上傳的文件的問題；
- [#700](https://github.com/hyperf-cloud/hyperf/pull/700) 修復 `Hyperf\HttpServer\Contract\ResponseInterface` 的 `download` 方法不能按預期運行的問題；
- [#701](https://github.com/hyperf-cloud/hyperf/pull/701) 修復自定義進程在出現未捕獲的異常時不會自動重啓的問題；
- [#704](https://github.com/hyperf-cloud/hyperf/pull/704) 修復 `Hyperf\Validation\Middleware\ValidationMiddleware` 在 action 參數沒有定義參數類型時會報錯的問題；
- [#713](https://github.com/hyperf-cloud/hyperf/pull/713) 修復當開啓了註解緩存功能是，`ignoreAnnotations` 不能按預期工作的問題；
- [#717](https://github.com/hyperf-cloud/hyperf/pull/717) 修復 `getValidatorInstance` 方法會重複創建驗證器對象的問題；
- [#724](https://github.com/hyperf-cloud/hyperf/pull/724) 修復 `db:seed` 命令在沒有傳 `database` 參數時會報錯的問題；
- [#729](https://github.com/hyperf-cloud/hyperf/pull/729) 修正組件配置項 `db:model` 為 `gen:model`；
- [#737](https://github.com/hyperf-cloud/hyperf/pull/737) 修復非 Worker 進程下無法使用 Tracer 組件來追蹤調用鏈的問題；

# v1.1.1 - 2019-10-08

## Fixed

- [#664](https://github.com/hyperf/hyperf/pull/664) 調整通過 `gen:request` 命令生成 FormRequest 時 `authorize` 方法的默認返回值；
- [#665](https://github.com/hyperf/hyperf/pull/665) 修復啓動時永遠會自動生成代理類的問題；
- [#667](https://github.com/hyperf/hyperf/pull/667) 修復當訪問一個不存在的路由時 `Hyperf\Validation\Middleware\ValidationMiddleware` 會拋出異常的問題；
- [#672](https://github.com/hyperf/hyperf/pull/672) 修復當 Action 方法上的參數類型為非對象類型時 `Hyperf\Validation\Middleware\ValidationMiddleware` 會拋出一個未捕獲的異常的問題；
- [#674](https://github.com/hyperf/hyperf/pull/674) 修復使用 `gen:model` 命令從數據庫生成模型時模型表名錯誤的問題；

# v1.1.0 - 2019-10-08

## 新增

- [#401](https://github.com/hyperf/hyperf/pull/401) 新增了 `Hyperf\HttpServer\Router\Dispatched` 對象來儲存解析的路由信息，在用户中間件之前便解析完成以便後續的使用，同時也修復了路由裏帶參時中間件失效的問題；
- [#402](https://github.com/hyperf/hyperf/pull/402) 新增 `@AsyncQueueMessage` 註解，通過定義此註解在方法上，表明這個方法的實際運行邏輯是投遞給 Async-Queue 隊列去消費；
- [#418](https://github.com/hyperf/hyperf/pull/418) 允許發送 WebSocket 消息到任意的 fd，即使當前的 Worker 進程不持有對應的 fd，框架會自動進行進程間通訊來實現發送；
- [#420](https://github.com/hyperf/hyperf/pull/420) 為數據庫模型增加新的事件機制，與 PSR-15 的事件調度器相配合，可以解耦的定義 Listener 來監聽模型事件；
- [#429](https://github.com/hyperf/hyperf/pull/429) [#643](https://github.com/hyperf/hyperf/pull/643) 新增 Validation 表單驗證器組件，這是一個衍生於 [illuminate/validation](https://github.com/illuminate/validation) 的組件，感謝 Laravel 開發組提供如此好用的驗證器組件，；
- [#441](https://github.com/hyperf/hyperf/pull/441) 當 Redis 連接處於低使用頻率的情況下自動關閉空閒連接；
- [#478](https://github.com/hyperf/hyperf/pull/441) 更好的適配 OpenTracing 協議，同時適配 [Jaeger](https://www.jaegertracing.io/)，Jaeger 是一款優秀的開源的端對端分佈式調用鏈追蹤系統；
- [#500](https://github.com/hyperf/hyperf/pull/499) 為 `Hyperf\HttpServer\Contract\ResponseInterface` 增加鏈式方法調用支持，解決調用了代理方法的方法後無法再調用原始方法的問題；
- [#523](https://github.com/hyperf/hyperf/pull/523) 為  `gen:model` 命令新增了 `table-mapping` 選項；
- [#555](https://github.com/hyperf/hyperf/pull/555) 新增了一個全局函數 `swoole_hook_flags` 來獲取由常量 `SWOOLE_HOOK_FLAGS` 所定義的 Runtime Hook 等級，您可以在 `bin/hyperf.php` 通過 `! defined('SWOOLE_HOOK_FLAGS') && define('SWOOLE_HOOK_FLAGS', SWOOLE_HOOK_ALL);` 的方式來定義該常量，即 Runtime Hook 等級；
- [#596](https://github.com/hyperf/hyperf/pull/596)  為`@Inject` 註解增加了  `required` 參數，當您定義 `@Inject(required=false)` 註解到一個成員屬性上，那麼當該依賴項不存在時也不會拋出 `Hyperf\Di\Exception\NotFoundException` 異常，而是以默認值 `null` 來注入， `required` 參數的默認值為 `true`，當在構造器注入的情況下，您可以通過對構造器的參數定義為 `nullable` 來達到同樣的目的；
- [#597](https://github.com/hyperf/hyperf/pull/597) 為 AsyncQueue 組件的消費者增加 `Concurrent` 來控制消費速率；
- [#599](https://github.com/hyperf/hyperf/pull/599) 為 AsyncQueue 組件的消費者增加根據當前重試次數來設定該消息的重試等待時長的功能，可以為消息設置階梯式的重試等待；
- [#619](https://github.com/hyperf/hyperf/pull/619) 為 Guzzle 客户端增加 HandlerStackFactory 類，以便更便捷地創建一個 HandlerStack；
- [#620](https://github.com/hyperf/hyperf/pull/620) 為 AsyncQueue 組件的消費者增加自動重啓的機制；
- [#629](https://github.com/hyperf/hyperf/pull/629) 允許通過配置文件的形式為 Apollo 客户端定義  `clientIp`, `pullTimeout`, `intervalTimeout` 配置；
- [#647](https://github.com/hyperf/hyperf/pull/647) 根據 server 的配置，自動為 TCP Response 追加 `eof`；
- [#648](https://github.com/hyperf/hyperf/pull/648) 為 AMQP Consumer 增加 `nack` 的返回類型，當消費邏輯返回 `Hyperf\Amqp\Result::NACK` 時抽象消費者會以 `basic_nack` 方法來響應消息；
- [#654](https://github.com/hyperf/hyperf/pull/654) 增加所有 Swoole Event 的默認回調和對應的 Hyperf 事件；

## 變更

- [#437](https://github.com/hyperf/hyperf/pull/437) `Hyperf\Testing\Client` 在遇到異常時不再直接拋出異常而是交給 ExceptionHandler 流程處理；
- [#463](https://github.com/hyperf/hyperf/pull/463) 簡化了 `container.php` 文件及優化了註解緩存機制；

新的 config/container.php 文件內容如下：

```php
<?php

use Hyperf\Di\Container;
use Hyperf\Di\Definition\DefinitionSourceFactory;
use Hyperf\Context\ApplicationContext;

$container = new Container((new DefinitionSourceFactory(true))());

if (! $container instanceof \Psr\Container\ContainerInterface) {
    throw new RuntimeException('The dependency injection container is invalid.');
}
return ApplicationContext::setContainer($container);
```

- [#486](https://github.com/hyperf/hyperf/pull/486) `Hyperf\HttpMessage\Server\Request` 的 `getParsedBody` 方法現在可以直接處理 JSON 格式的數據了；
- [#523](https://github.com/hyperf/hyperf/pull/523) 調整 `gen:model` 命令生成的模型類名默認為單數，如果表名為複數，則默認生成的類名為單數；
- [#614](https://github.com/hyperf/hyperf/pull/614) [#617](https://github.com/hyperf/hyperf/pull/617) 調整了 ConfigProvider 類的結構, 同時將 `config/dependencies.php` 文件移動到了 `config/autoload/dependencies.php` 內，且文件結構去除了 `dependencies` 層，此後也意味着您也可以將 `dependencies` 配置寫到 `config/config.php` 文件內；

Config Provider 內數據結構的變化：
之前：

```php
'scan' => [
    'paths' => [
        __DIR__,
    ],
    'collectors' => [],
],
```

現在：

```php
'annotations' => [
    'scan' => [
        'paths' => [
            __DIR__,
        ],
        'collectors' => [],
    ],
],
```

> 增加了一層 annotations，這樣將與配置文件結構一致，不再特殊

- [#630](https://github.com/hyperf/hyperf/pull/630) 變更了 `Hyperf\HttpServer\CoreMiddleware` 類的實例化方式，使用 `make()` 來替代了 `new`；
- [#631](https://github.com/hyperf/hyperf/pull/631) 變更了 AMQP Consumer 的實例化方式，使用 `make()` 來替代了 `new`；
- [#637](https://github.com/hyperf/hyperf/pull/637) 調整了 `Hyperf\Contract\OnMessageInterface` 和 `Hyperf\Contract\OnOpenInterface` 的第一個參數的類型約束， 使用 `Swoole\WebSocket\Server` 替代 `Swoole\Server`；
- [#638](https://github.com/hyperf/hyperf/pull/638) 重命名了 `db:model` 命令為 `gen:model` 命令，同時增加了一個 Visitor 來優化創建的 `$connection` 成員屬性，如果要創建的模型類的 `$connection` 屬性的值與繼承的父類一致，那麼創建的模型類將不會包含此屬性；

## 移除

- [#401](https://github.com/hyperf/hyperf/pull/401) 移除了 `Hyperf\JsonRpc\HttpServerFactory`, `Hyperf\HttpServer\ServerFactory`, `Hyperf\GrpcServer\ServerFactory` 類；
- [#402](https://github.com/hyperf/hyperf/pull/402) 移除了棄用的 `AsyncQueue::delay` 方法；
- [#563](https://github.com/hyperf/hyperf/pull/563) 移除了棄用的 `Hyperf\Server\ServerInterface::SERVER_TCP` 常量，使用 `Hyperf\Server\ServerInterface::SERVER_BASE` 來替代；
- [#602](https://github.com/hyperf/hyperf/pull/602) 移除了 `Hyperf\Utils\Coroutine\Concurrent` 的 `timeout` 參數；
- [#612](https://github.com/hyperf/hyperf/pull/612) 移除了 RingPHP Handler 裏沒有使用到的 `$url` 變量；
- [#616](https://github.com/hyperf/hyperf/pull/616) [#618](https://github.com/hyperf/hyperf/pull/618) 移除了 Guzzle 裏一些無用的代碼；

## 優化

- [#644](https://github.com/hyperf/hyperf/pull/644) 優化了註解掃描的流程，分開 `app` 和 `vendor` 兩部分來掃描註解，大大減少了用户的掃描耗時；
- [#653](https://github.com/hyperf/hyperf/pull/653) 優化了 Swoole shortname 的檢測邏輯，現在的檢測邏輯更加貼合 Swoole 的實際配置場景，也不只是 `swoole.use_shortname = "Off"` 才能通過檢測了；

## 修復

- [#448](https://github.com/hyperf/hyperf/pull/448) 修復了當 HTTP Server 或 WebSocket Server 存在時，TCP Server 有可能無法啓動的問題；
- [#623](https://github.com/hyperf/hyperf/pull/623) 修復了當傳遞一個 `null` 值到代理類的方法參數時，方法仍然會獲取方法默認值的問題；
