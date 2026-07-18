# Bug：手机点击打印没效果

## 现象

手机上点「打印」无明显反应（无系统打印框，或空白页）。

## 原因

1. **用户手势链断裂**：点击后先 `setMode` / 大段 DOM 更新再 `window.print()`，iOS Safari / 部分 WebView 会静默忽略 print。  
2. **复杂页打印裁切**：`.panel { overflow: hidden }`、祖先 `display:none` 等导致打印空白。  
3. **内置浏览器限制**：微信等 WebView 可能禁用或弱化 `window.print`。

## 修复

1. 打印 CSS：`overflow: visible`；日/周面板在 print 下强制显示对应内容。  
2. 统一 `triggerPrint({ week })`：  
   - **手机/触屏**：用隐藏 **iframe** 写入 `#planSheet` / `#weekSheet` 再 `print()`（不依赖整页布局）。  
   - **桌面**：仍 `window.print()` 整页；失败则回退 iframe。  
3. 空预览时 toast 提示先填内容；无法打印时提示改用 MD/TXT。  
4. 尽量不在 print 前强制 `setMode`，避免打断手势。

## 验收

1. 手机 Chrome / Safari：有内容时点打印 → 出现系统打印/分享面板。  
2. 预览为空时有提示。  
3. 桌面打印日/周仍正常。  
4. 微信内若仍被禁：应有 toast 引导用系统浏览器或导出 MD/TXT。  
