# 接口

源码见[github](https://github.com/StellarCN/firefly/blob/master/src/api/ffw.js)

## 接口代码整理说明
```
  /**
 * 接口根对象
 */
window.FFW = {

  /**
   * 当前钱包版本号（v2.1.0添加，未正式上线）
   */
  version:'2.1.0',
  /**
   * 当前钱包的操作系统，ios或android，（v2.1.0添加，未正式上线）
   */
  platform: 'ios',

  /**
   * 属性，String类型
   * 当前打开DAPP的钱包的登陆账户公钥地址
   */
  address: 'GCENG5GLJ35GPJZQM3YJSFL3GMQ57MA5U6ZAAE6V4XIFVXFPY5MS5Q65',
  /**
   * 属性，Array类型
   * 当前打开DAPP的钱包的联系人信息
   */
  contacts: [{
    name: '自己',
    address:'GCENG5GLJ35GPJZQM3YJSFL3GMQ57MA5U6ZAAE6V4XIFVXFPY5MS5Q65',
    memotype:'TEXT',
    memo:'测试备注'
  }],

  /**
   * 属性，Array类型
   * 当前打开DAPP的钱包的地址簿
   */
  myaddresses: [{
    name:'btc',
    address:'mybtcaddress',
    memo:'我的BTC地址'
  }],

  /**
   * 支付方法
   * @param {Object} data 参数
   *  data: {
   *    destination: '接收方的公钥G地址', 
   *    code: '资产编码', 
   *    issuer: '资产发行方', 
   *    amount: '资产发送数量，number类型', 
   *    memo_type: '备注类型，可取值：NONE TEXT HASH ID RETURN', 
   *    memo: '备注'
   *  }
   * @param {string,function} callback 回调函数，可以是函数名称也可以是函数，
   *      回调函数接收一个对象
   *        {
   *            code:'可取fail或success,false表示失败，success表示处理成功',
   *            message:'提示信息',
   *            data:'返回结果数据，是object类型，可能为null'
   *          }
   * 示例：
   *   FFW.pay({
   *      destination: 'GBFGPA6MELXHEKWPJW75LOMC4CHGHTZ67LOWUGTUUILMXMZZGFLTO3X7', 
   *      code: 'XFF', 
   *      issuer: 'GAZEX2USUBMMWFRZFS77VDJYXUFLXI4ZGFPWX6TBNZCSTEQWNLFZMXFF', 
   *      amount: 100, 
   *      memo_type: 'TEXT', 
   *      memo: 'Hello,FFW'
   *    }, function(response){
   *        if(response.code === 'fail'){
   *          console.log('error:' + response.message)  
   *        }else{
   *          console.log('pay success')
   *        }
   *    })
   */
  pay(data, callback){
    // code
  },

  /**
   * 路径支付方法
   * @param {Object} data 参数
   *  data: {
   *    destination: '接收方的公钥G地址', 
   *    code: '资产编码', 
   *    issuer: '资产发行方', 
   *    amount: '资产发送数量，number类型', 
   *    memo_type: '备注类型，可取值：NONE TEXT HASH ID RETURN', 
   *    memo: '备注'
   *  }
   * @param {string或function} callback 回调函数，可以是函数名称也可以是函数
   *      回调函数接收一个对象
   *        {
   *            code:'可取fail或success,false表示失败，success表示处理成功',
   *            message:'提示信息',
   *            data:'返回结果数据，是object类型，可能为null'
   *          }
   * 示例：
   *   FFW.pathPayment({
   *      destination: 'GBFGPA6MELXHEKWPJW75LOMC4CHGHTZ67LOWUGTUUILMXMZZGFLTO3X7', 
   *      code: 'XFF', 
   *      issuer: 'GAZEX2USUBMMWFRZFS77VDJYXUFLXI4ZGFPWX6TBNZCSTEQWNLFZMXFF', 
   *      amount: 100, 
   *      memo_type: 'TEXT', 
   *      memo: 'Hello,FFW'
   *    }, function(response){
   *        if(response.code === 'fail'){
   *          console.log('error:' + response.message)  
   *        }else{
   *          console.log('success')
   *        }
   *    })
   */
  pathPayment(data, callback){
    //code
  },

  /**
   * 对数据进行签名，主要是针对一些数据进行签名，方便后台应用确认当前操作人员具有账户的权限，防止恶意请求
   * @param {String} data 要进行签名的数据，必须为json数据类型，然后转为String格式，由于json数据转到后台之后，要保证后台取的json数据和前台的json数据格式字段顺序一致，否则会校验失败
   * @param {string或function} callback 回调函数，可以是函数名称也可以是函数
   *      回调函数接收一个对象
   *        {
   *            code:'可取fail或success,false表示失败，success表示处理成功',
   *            message:'提示信息',
   *            data:'返回结果数据，是string类型，返回签名完成后数据的base64结果'
   *          }
   *    示例：
   *    let data = {name: 'firefly wallet dapp'}
   *    data = JSON.stringify(data)
   *    FFW.sign(data, function(response){
   *        if(response.code === 'fail'){
   *          console.log('error:' + response.message)  
   *        }else{
   *          console.log('do success')
   *          console.log('对{name: "firefly wallet dapp"}签名后的结果：'+response.data)
   *        }
   *    })
   */
  sign(data, callback){
    //code
  },

  /**
   * 针对transaction生成的xdr进行签名，生成可提交到horizon的transaction xdr
   * @param {string} data 必须为transaction生成的xdr 
   * @param {string或function} callback ,回调函数，可以是函数名称也可以是函数
   *      回调函数接收一个对象
   *        {
   *            code:'可取fail或success,false表示失败，success表示处理成功',
   *            message:'提示信息',
   *            data:'返回结果数据，是string类型，返回签名完成后transaction对应的xdr'
   *          }
   * 示例：
   *   let xdr = 'AAAAAEpng8wi7nIqz02/1bmC4I5jzz763WoadKIWy7M5MVc3AAAAZACHjkkAAAABAAAAAAAAAAAAAAABAAAAAAAAAAoAAAALaG9tZV9kb21haW4AAAAAAQAAABBodHRwOi8vZmNoYWluLmlvAAAAAAAAAAA='
   *   FFW.signXDR(xdr, function(response){
   *        if(response.code === 'fail'){
   *          console.log('error:' + response.message)  
   *        }else{
   *          console.log('do success')
   *          console.log('对XDR签名后的XDR结果：'+response.data)
   *        }
   *    })
   */
  signXDR(data, callback){
    // code
  },
  /**
   * 备份数据，备份当前用户的contact和myaddress
   * @param {string或function} callback 回调函数，可以是函数名称也可以是函数
   *      回调函数接收一个对象
   *        {
   *            code:'可取fail或success,false表示失败，success表示处理成功',
   *            message:'提示信息',
   *            data:'返回结果数据，是string类型，返回对contact和myaddress加密后的数据,可以直接保存该结果到系统中'
   *          }
   * 示例：
   *   FFW.backup(function(response){
   *        if(response.code === 'fail'){
   *          console.log('error:' + response.message)  
   *        }else{
   *          console.log('do success')
   *          console.log('加密后的备份数据：'+response.data)
   *        }
   *    })
   */
  backup(callback){
    //code
  },

  /**
   * 恢复数据函数，根据backup函数加密备份后的数据，重新恢复到当前钱包中进行覆盖
   * @param {string} data 
   * @param {string或function} callback 回调函数，可以是函数名称也可以是函数
   *      回调函数接收一个对象
   *        {
   *            code:'可取fail或success,false表示失败，success表示处理成功',
   *            message:'提示信息'
   *          }
   * 示例：
   *   //其中，data是backup备份操作后拿到的数据
   *   FFW.recovery(data,function(response){
   *        if(response.code === 'fail'){
   *          console.log('error:' + response.message)  
   *        }else{
   *          console.log('do success')
   *        }
   *    })
   */
  recovery(data, callback){
    //code
  },
  /**
   * 授信资产
   * @param {string} code 资产编码
   * @param {string} issuer 资产发行方 
   * @param {string或function} callback 回调函数，可以是函数名称，也可以是函数
   *      回调函数接收一个对象
   *        {
   *            code:'可取fail或success,false表示失败，success表示处理成功',
   *            message:'提示信息'
   *          }
   * 示例：
   *   let code = 'XFF';
   *   let issuer = 'GAZEX2USUBMMWFRZFS77VDJYXUFLXI4ZGFPWX6TBNZCSTEQWNLFZMXFF';
   *   FFW.trust(code,issuer,function(response){
   *        if(response.code === 'fail'){
   *          console.log('error:' + response.message)  
   *        }else{
   *          console.log('do success')
   *        }
   *    })
   */
  trust(code, issuer, callback){
    //code
  }
}
```
