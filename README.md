2021/12 change big QFP100 cpld so need update fw to support it.
if cpld update fail,don't shutdown_base

bool init() {
        set_idivc_base_clocks(cgu::CLK_SEL::IDIVC);

        i2c0.start(i2c_config_boot_clock);

        if( !portapack::cpld::update_if_necessary(portapack_cpld_config()) ) {
                //shutdown_base();
                //return false;
        }

