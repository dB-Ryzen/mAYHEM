### ChibiOS initialization sequence

On the Cortex-M0 core, boot time looks like this:

    ResetHandler:
        Initialize FPU (only for the Cortex-M4F)
        Initialize stacks (fill with pattern)
        __early_init()
            Enable extra processor exceptions for debugging
        Init data segment (flash -> data)
        Initialize BSS (fill with 0)
        __late_init()
            reset_peripherals()
            halInit()
                hal_lld_init()
                    Init timer 3 as cycle counter
                    Init RIT as SysTick
                palInit()
                gptInit()
                i2cInit()
                sdcInit()
                spiInit()
                rtcInit()
                boardInit()
            chSysInit()
        Constructors
        main()
        Destructors
        _default_exit() (default is infinite loop)
