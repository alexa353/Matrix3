idf_component_register(
    SRCS
        "main.c"
        "system.c"
        "i2c_bitaxe.c"
        "nvs_config.c"
        "device_config.c"
        "adc.c"
        "display.c"
        "screen.c"
        "input.c"
        "work_queue.c"
        "./power/asic_reset.c"
        "./tasks/asic_result_task.c"
        "./tasks/stratum_task.c"
        "./tasks/create_jobs_task.c"
        "./tasks/power_management_task.c"
        "./tasks/fan_controller_task.c"
        "./tasks/statistics_task.c"
        "./tasks/hashrate_monitor_task.c"
        "./http_server/http_server.c"
        "./http_server/theme_api.c"
        "./http_server/websocket.c"
        "./power/power.c"
        "./power/vcore.c"
        "./power/INA260.c"
    INCLUDE_DIRS
        "." 
        "tasks" 
        "power" 
        "thermal"     # <--- DAS HAT GEFEHLT (Fix für thermal.h)
        "http_server"
        "../components/asic/include"
        "../components/stratum/include"
    REQUIRES
        "connect" 
        "asic"
        "stratum" 
        "esp_http_server" 
        "nvs_flash"
        "esp_netif" 
        "esp_event" 
        "esp_psram" 
        "esp_lcd"
        "lvgl__lvgl"
    PRIV_REQUIRES
        "driver" 
        "esp_adc" 
        "esp_driver_i2c" 
        "json" 
        "spiffs"
        "app_update"
    EMBED_FILES 
        "./http_server/recovery_page.html"
)

# --- LVGL & COMPILER FIXES ---
idf_build_set_property(COMPILE_OPTIONS "-DLV_CONF_INCLUDE_SIMPLE=1" APPEND)
idf_build_set_property(COMPILE_OPTIONS "-DLV_CONF_PATH=\"${CMAKE_SOURCE_DIR}/main/lv_conf.h\"" APPEND)

# Warnungen ignorieren
idf_build_set_property(COMPILE_OPTIONS "-Wno-error=all" APPEND)
