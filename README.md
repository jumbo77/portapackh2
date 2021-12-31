2021/12 change big QFP100 cpld so need update fw to support it.                                                         
if cpld update fail,don't shutdown_base                                                         
to update v1.4.2 :                                                              
1.HackRF Press DFU then Press RESET                                                             
2.Click dfu_hackrf_one.bat                                                              
3.Then Click flash_portapack_mayhem_skip_cpld1.4.2.bat                                                          
4.update Finished                                                               
                                                                
I just Change the mayhem code to support portack cpld flashed QFP100 Chip.                                                              
A and B                                                         
bool init() {                                                           
        set_idivc_base_clocks(cgu::CLK_SEL::IDIVC);
                                                                
        i2c0.start(i2c_config_boot_clock);
                                                                
        if( !portapack::cpld::update_if_necessary(portapack_cpld_config()) ) {                                                                  
                A//shutdown_base();
                B//return false;
        }

