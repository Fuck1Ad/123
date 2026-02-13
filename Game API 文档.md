# Game API 文档

`window.gameapi` 提供了游戏过程中主要变量和辅助函数的访问接口。

## 主要状态

| 变量名 | 类型 | 说明 |
|--------|------|------|
| `state` | `GameState` | 完整游戏状态对象 |
| `phase` | `Phase` | 当前游戏阶段 (如 SUMMER, SEMESTER_1, ENDING 等) |
| `week` | `number` | 当前周数 |
| `totalWeeksInPhase` | `number` | 当前阶段总周数 |
| `isPlaying` | `boolean` | 是否正在自动进行游戏 |
| `isWeekend` | `boolean` | 是否为周末 |
| `weekendActionPoints` | `number` | 周末剩余行动点数 |

## 综合属性

| 变量名 | 类型 | 说明 |
|--------|------|------|
| `general` | `GeneralStats` | 综合属性 {心态, 经验, 运气, 魅力, 健康, 金钱, 效率} |
| `initialGeneral` | `GeneralStats` | 初始综合属性 |

## 科目系统

| 变量名 | 类型 | 说明 |
|--------|------|------|
| `subjects` | `Record<SubjectKey, SubjectStats>` | 各科目状态 {aptitude, level} |
| `selectedSubjects` | `SubjectKey[]` | 已选科目列表 |

## OI 竞赛系统

| 变量名 | 类型 | 说明 |
|--------|------|------|
| `oiStats` | `OIStats` | OI能力 {dp, ds, math, string, graph, misc} |
| `competition` | `CompetitionType` | 竞赛类型 ('None', 'OI', 'MO', 'PhO', 'ChO') |
| `competitionResults` | `CompetitionResultData[]` | 竞赛结果历史 |

## 社交与活动

| 变量名 | 类型 | 说明 |
|--------|------|------|
| `club` | `ClubId \| null` | 当前社团 |
| `romancePartner` | `string \| null` | 恋爱对象 |
| `className` | `string` | 班级名称 |

## 事件系统

| 变量名 | 类型 | 说明 |
|--------|------|------|
| `currentEvent` | `GameEvent \| null` | 当前事件 |
| `chainedEvent` | `GameEvent \| null` | 链接事件 (下一事件) |
| `eventResult` | `EventResult \| null` | 事件执行结果 |
| `eventQueue` | `GameEvent[]` | 事件队列 |

## 考试系统

| 变量名 | 类型 | 说明 |
|--------|------|------|
| `examResult` | `ExamResult \| null` | 考试结果 |
| `midtermRank` | `number \| null` | 期中考试排名 |
| `popupExamResult` | `ExamResult \| null` | 弹窗显示的考试结果 |
| `popupCompetitionResult` | `CompetitionResultData \| null` | 弹窗显示的竞赛结果 |

## 成就与挑战

| 变量名 | 类型 | 说明 |
|--------|------|------|
| `difficulty` | `Difficulty` | 难度 (NORMAL, HARD, REALITY, AI_STORY, CUSTOM) |
| `activeChallengeId` | `string \| null` | 活跃挑战ID |
| `unlockedAchievements` | `string[]` | 已解锁成就ID列表 |
| `achievementPopup` | `Achievement \| null` | 成就弹窗显示 |

## 角色状态

| 变量名 | 类型 | 说明 |
|--------|------|------|
| `activeStatuses` | `GameStatus[]` | 活跃状态列表 (增益/减益) |
| `isSick` | `boolean` | 是否生病 |
| `isGrounded` | `boolean` | 是否被禁足 |
| `debugMode` | `boolean` | 调试模式 (当前未使用) |
| `sleepCount` | `number` | 睡觉次数 |
| `rejectionCount` | `number` | 被拒绝次数 |

## 天赋与物品

| 变量名 | 类型 | 说明 |
|--------|------|------|
| `talents` | `Talent[]` | 天赋列表 |
| `inventory` | `string[]` | 物品栏 (物品ID列表) |

## 其他状态

| 变量名 | 类型 | 说明 |
|--------|------|------|
| `theme` | `Theme` | 主题 ('light' 或 'dark') |
| `log` | `GameLogEntry[]` | 游戏日志 |
| `history` | `StoryEntry[]` | 故事历程 |
| `triggeredEvents` | `string[]` | 已触发事件ID列表 |
| `recentEventIds` | `string[]` | 最近事件ID (防重复) |
| `aiBuffer` | `GameEvent[]` | AI生成事件缓冲区 |
| `isAiGenerating` | `boolean` | 是否正在AI生成中 |

## 辅助函数

### `saveGame()`
保存游戏进度到本地存储。

```javascript
window.gameapi.saveGame()
