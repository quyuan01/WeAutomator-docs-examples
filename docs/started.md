# WeAutomator入手教程
1. ##组织用例-以pytest为例
import pytest
class TestPhone(object):
    def setup_class(self):
        """
        每个测试类运行之前执行一次,初始化类
        """
        #初始化设备驱动和环境，必填
        init_driver(workspace=os.path.dirname(__file__))
        #预先处理弹窗
        start_event_handler()
        #返回home页
        press(DeviceButton.HOME)

    def teardown_class(self):
        """
        每个测试类运行之后执行一次
        """
        press(DeviceButton.HOME)
        stop_driver()
    
    def setup_method(self, method):
        """
        每个用例开始前初始化
        """
        #启动app
        pkg = "com.tencent.qqpimsecure"
        uninstall_app(pkg)
        #安卓app,app_path填写app本地路径
        install_app(app_path)
        #启动app，清理上一次遗留的数据
        start_app(pkg, clear_data=True)
       
    def teardown_method(self, method):
        """
        每个用例结束后执行
        """
        pass
        
    def test_case_1(self):
        """
        测试case 1 
        """
        pass
        
    def test_case_2(self):
        """
        测试case 2
        """
        pass
        
pytest_main([os.path.join(os.path.dirname(__file__), "main.py")])

        
