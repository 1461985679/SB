# 选购证据和归档结构

正式归档时使用本参考。根据任务规模删减空目录，不要制造没有证据的占位文件。

## 平台采样统计字段

| 字段 | 说明 |
|---|---|
| platform | 平台名称 |
| login_verified_at | 登录状态核对时间 |
| route | comprehensive、low_price或high_price |
| raw_seen | 原始浏览数量 |
| invalid_count | 无效商品数量 |
| duplicate_count | 重复商品数量 |
| route_unique_contribution | 该路线新增的去重商品数量 |
| platform_unique_total | 平台内去重商品总数 |
| target_count | 平台目标数量，通常为200或300 |
| supply_exhausted | 是否已经到达实际供给终点 |
| shortage_evidence | 供给不足时的页面证据和说明 |

## 商品数据字段

| 字段 | 说明 |
|---|---|
| source_id | 稳定来源编号，例如P1、T1、J1 |
| platform | 平台或官网 |
| sort_route | comprehensive、low_price或high_price |
| route_rank | 商品在排序路线中的位置 |
| seller | 店铺或销售方 |
| brand | 品牌 |
| product | 商品名称 |
| model_variant | 型号和准确规格 |
| product_id | 平台商品编号 |
| platform_dedupe_key | 品牌、型号、规格、版本组成的平台内去重键 |
| cross_platform_key | 跨平台同型号合并键 |
| duplicate_of | 重复记录指向的主记录编号 |
| observed_price | 抓取时页面价格 |
| price_conditions | 券、会员、地区、账号、运费和组合条件 |
| usable_quantity | 可比较的总数量 |
| unit_price | 统一单位价格和计算式 |
| hard_pass | 是否满足全部硬条件 |
| ideal_pass | 是否进入理想区间 |
| quality_evidence | 核心质量数据和证据等级 |
| exclusion_reason | 排除理由 |
| original_url | 原始链接 |
| final_url | 跳转后的最终链接 |
| captured_at | 带时区的抓取时间 |
| full_screenshot | 整页长截图路径 |
| key_screenshot | 关键数据截图路径 |
| text_snapshot | DOM或文本快照路径 |
| notes | 遮蔽、登录、风险验证和其他限制 |

## 标准数据字段

| 字段 | 说明 |
|---|---|
| criterion | 指标名称 |
| direction | 不低于、不高于、等于或区间 |
| pass_value | 及格线 |
| ideal_range | 理想区间 |
| unit | 单位 |
| hard_requirement | 是否属于硬条件 |
| source_id | 标准来源编号 |
| evidence_location | 来源页面和本地截图位置 |

## 建议归档目录

```text
选购归档_日期
  01_标准
  02_平台采样清单
  03_历史报告
  04_当前报告
  05_数据与链接
  06_核验记录
  07_网页快照
    标准来源
    推荐商品
    排除商品
    页面文本快照
    网页快照索引.html
    网页快照清单.csv
    文件校验值_SHA256.csv
```

## 去重口径

平台内去重键用于执行每个平台的最低采样量。同一商品在不同店铺、广告位、活动页或排序路线重复出现时，只计一次。排序路线的重叠商品保留记录，但不增加新路线贡献数。

跨平台产品键用于最终比较。同一型号在不同平台销售时，合并为一个产品和多个报价。各平台覆盖统计仍然分别保留。

## 引用粒度

来源编号证明页面身份。本地证据编号证明具体画面。推荐使用P6E1表示完整商品页，P6E2表示关键规格或性能截图。计算结果同时引用输入来源和计算式。

## 截图完整性

整页截图用于保存网页上下文。关键截图用于证明具体数字。轮播图和懒加载内容需要逐页激活后保存。长图用于快速审阅，单张图用于精确引用。原始资源和截图均存在时，两个版本都保留。

## 价格边界

记录价格观察时间。完整数字被问号、星号、登录页或风险验证遮蔽时，不得恢复或猜测。历史价格可以保留，但必须标注历史观察日期，并且要求购买前复核。
