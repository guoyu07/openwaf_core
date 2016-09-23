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
* [register_order_modules](#register_order_modules)
* [register_modules](#register_modules)
* [get_default_config_param](#get_default_config_param)
* [get_config_param](#get_config_param)
* [get_modules_config_param](#get_modules_config_param)
* [run](#run)

new
---
**syntax:** *twaf = new(config, logger)*

get_init_config_param
---------------------
**syntax:** *twaf:get_init_config_param(key)*

register_order_modules
----------------------
**syntax:** *twaf:register_order_modules(phase_order)*

register_modules
----------------
**syntax:** *twaf:register_modules(module_name, path)*

ctx
---
**syntax:** *ctx = twaf:ctx()*

get_config_param
----------------
**syntax:** *cf = twaf:get_config_param(module_name)*

run
----------------
**syntax:** *twaf:run()*
