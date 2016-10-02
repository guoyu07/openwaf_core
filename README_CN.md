Synopsis
========
```lua
    -- app/openwaf_init.lua
    -- construct a new object - twaf
    local twaf_lib = require "lib.twaf.core"
    twaf = twaf_lib:new(twaf_config, twaf_logger)
    
    local access_order = twaf:get_init_config_param("access_order")
    for _, modules in pairs(access_order) do
        local modules_name, path = next(modules)
        twaf:register_order_modules("access", modules_name, path)
    end
    
    local init_register = twaf:get_init_config_param("init_register")
    for modules_name, path in pairs(init_register) do
        twaf:register_modules(modules_name, path)
    end
```

Directives
================================
* [new](#new)
* [ctx](#ctx)
* [register_modules](#register_modules)
* [get_default_config_param](#get_default_config_param)
* [get_config_param](#get_config_param)
* [get_modules_config_param](#get_modules_config_param)
* [run](#run)

new
---
**syntax:** *twaf = require"twaf_core"：new(config)*

用于初始化新的对象，同时初始化配置

ctx
---
**syntax:** *ctx = twaf:ctx()*

用于存放当前请求的临时信息

register_modules
----------------
**syntax:** *twaf:register_modules({module_name:path})*

模块注册

例如：
```lua
local modules = {anti_hotlink = "lib.twaf.anti_hotlink",
                 anti_robot   = "lib.twaf.anti_robot"}
                 
twaf:register_modules(modules)
```

get_default_config_param
------------------------
**syntax:** *twaf:get_default_config_param(key)*

获取缺省配置

get_config_param
----------------
**syntax:** *cf = twaf:get_config_param(module_name)*

获取策略一级配置

get_modules_config_param
----------------
**syntax:** *cf = twaf:get_modules_config_param(module_name, param)*

获取策略二级配置

run
----------------
**syntax:** *twaf:run()*

执行模块
