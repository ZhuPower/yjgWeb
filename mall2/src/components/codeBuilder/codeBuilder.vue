<template>
  <div class="codeBuilderWrap">
      <h2>专题页代码生成器</h2>
      <form>
        <ul class="ul">
            <li>
                <span>客户端：</span>
                <select ref="client" v-model="clientKey">
                  <option value="0">请选择</option>
                  <option value="pc">PC端</option>
                  <option value="app">app端</option>
                </select>
                <span>栏目：</span>
                <select ref="column" v-model="columnKey">
                    <option value="0">请选择</option>
                </select>
                <span>模板：</span>
                <select ref="template" v-model="templateKey">
                    <option value="0">请选择</option>
                </select>
            </li>
            <li><span>背景：</span><input type="text" v-model="background"></li>
            <li>
              <span>头图：</span>
              <input type="text" class="banner" v-model="banner">
              <input type="button"  value="上传图片" class="upBtn" @click="upBanner()" />
              <input type="file" accept="image/gif,image/jpeg,image/jpg,image/png" ref="fileBanner">
            </li>
            <li>
              <span>商品列表：</span>
              <div class="customizeWerap" ref="customizeWerap">
                <ul class="typeWrap">
                  <li>
                    <span>类型：</span>
                    <label>文本<input type="radio" v-model="typeTemplat" value="txt"/></label>
                    <label v-if="clientKey == 'app'">图片<input type="radio" v-model="typeTemplat" value="image"/></label>
                    <label>定时<input type="radio" v-model="typeTemplat" value="timing"/></label>
                  </li>
                  <li v-if="typeTemplat == 'image'">
                    <span>个数：</span>
                    <select ref="rowNum" v-model="rowNum">
                      <option value="1">一行一个</option>
                      <option value="2">一行两个</option>
                      <option value="3">一行三个</option>
                      <option value="4">一行四个</option>
                    </select>
                  </li>
                </ul>
                <a href="javascript:;" class="addPor" @click="addProduct()">添加</a>
                <div class="proTemplate" ref="proTemplate">
                  <div class="cList" v-if="typeTemplat == 'txt'">
                    <ul>
                      <li><span>商品ID：</span><input type="text" class="proId"></li>
                      <li><span>商品价格：</span><input type="text" class="price"></li>
                      <li class="oddWrap"><span>单数：</span><input type="checkbox" class="odd"/></li>
                      <li class="markWordWrap"><span>标识词：</span><input type="text" class="markWord"></li>
                      <li><span>样式代码：</span><input type="text" class="fontSize"></li>
                    </ul>
                    <a href="javascript:;" class="delPor">删除</a>
                  </div>
                  <div class="cList imageWrap" v-if="typeTemplat == 'image'">
                    <div class="col-1-list" v-if="rowNum == 1">
                      <div class="list">
                        <img src="../../assets/defaultProduct.jpg" />
                        <div class="site">
                          <label>图片链接：<input type="text" value="http://www.yijiago.com/promotion/app/rearEnd/mall/upload/defaultProduct.jpg" class="productImg"></label>
                          <label>商品链接：<input type="text" value="javascript:;"></label>
                          <label>优惠券ID：<input type="text"></label>
                          <input type="button"  value="上传" class="upBtn" />
                          <input type="file" accept="image/gif,image/jpeg,image/jpg,image/png" class="fileProduct">
                          </div>
                      </div>
                    </div>
                    <div class="col-2-list" v-if="rowNum == 2">
                      <div class="list">
                        <img src="../../assets/defaultProduct.jpg" />
                        <div class="site">
                          <label>图片链接：<input type="text" value="http://www.yijiago.com/promotion/app/rearEnd/mall/upload/defaultProduct.jpg" class="productImg"></label>
                          <label>商品链接：<input type="text" value="javascript:;"></label>
                          <label>优惠券ID：<input type="text"></label>
                          <input type="button"  value="上传" class="upBtn" />
                          <input type="file" accept="image/gif,image/jpeg,image/jpg,image/png" class="fileProduct">
                          </div>
                      </div>
                      <div class="list">
                        <img src="../../assets/defaultProduct.jpg" />
                        <div class="site">
                          <label>图片链接：<input type="text" value="http://www.yijiago.com/promotion/app/rearEnd/mall/upload/defaultProduct.jpg" class="productImg"></label>
                          <label>商品链接：<input type="text" value="javascript:;"></label>
                          <label>优惠券ID：<input type="text"></label>
                          <input type="button"  value="上传" class="upBtn" />
                          <input type="file" accept="image/gif,image/jpeg,image/jpg,image/png" class="fileProduct">
                          </div>
                      </div>
                    </div>
                    <div class="col-3-list" v-if="rowNum == 3">
                      <div class="list">
                        <img src="../../assets/defaultProduct.jpg" />
                        <div class="site">
                          <label>图片：<input type="text" value="http://www.yijiago.com/promotion/app/rearEnd/mall/upload/defaultProduct.jpg" class="productImg"></label>
                          <label>商品：<input type="text" value="javascript:;"></label>
                          <label>优惠券ID：<input type="text"></label>
                          <input type="button"  value="上传" class="upBtn" />
                          <input type="file" accept="image/gif,image/jpeg,image/jpg,image/png" class="fileProduct">
                          </div>
                      </div>
                      <div class="list">
                        <img src="../../assets/defaultProduct.jpg" />
                        <div class="site">
                          <label>图片：<input type="text" value="http://www.yijiago.com/promotion/app/rearEnd/mall/upload/defaultProduct.jpg" class="productImg"></label>
                          <label>商品：<input type="text" value="javascript:;"></label>
                          <label>优惠券ID：<input type="text"></label>
                          <input type="button"  value="上传" class="upBtn" />
                          <input type="file" accept="image/gif,image/jpeg,image/jpg,image/png" class="fileProduct">
                          </div>
                      </div>
                      <div class="list">
                        <img src="../../assets/defaultProduct.jpg" />
                        <div class="site">
                          <label>图片：<input type="text" value="http://www.yijiago.com/promotion/app/rearEnd/mall/upload/defaultProduct.jpg" class="productImg"></label>
                          <label>商品：<input type="text" value="javascript:;"></label>
                          <label>优惠券ID：<input type="text"></label>
                          <input type="button"  value="上传" class="upBtn" />
                          <input type="file" accept="image/gif,image/jpeg,image/jpg,image/png" class="fileProduct">
                          </div>
                      </div>
                    </div>
                    <div class="col-4-list" v-if="rowNum == 4">
                      <div class="list">
                        <img src="../../assets/defaultProduct.jpg" />
                        <div class="site">
                          <label>图片：<input type="text" value="http://www.yijiago.com/promotion/app/rearEnd/mall/upload/defaultProduct.jpg" class="productImg"></label>
                          <label>商品：<input type="text" value="javascript:;"></label>
                          <label>优惠券ID：<input type="text"></label>
                          <input type="button"  value="上传" class="upBtn" />
                          <input type="file" accept="image/gif,image/jpeg,image/jpg,image/png" class="fileProduct">
                          </div>
                      </div>
                      <div class="list">
                        <img src="../../assets/defaultProduct.jpg" />
                        <div class="site">
                          <label>图片：<input type="text" value="http://www.yijiago.com/promotion/app/rearEnd/mall/upload/defaultProduct.jpg" class="productImg"></label>
                          <label>商品：<input type="text" value="javascript:;"></label>
                          <label>优惠券ID：<input type="text"></label>
                          <input type="button"  value="上传" class="upBtn" />
                          <input type="file" accept="image/gif,image/jpeg,image/jpg,image/png" class="fileProduct">
                          </div>
                      </div>
                      <div class="list">
                        <img src="../../assets/defaultProduct.jpg" />
                        <div class="site">
                          <label>图片：<input type="text" value="http://www.yijiago.com/promotion/app/rearEnd/mall/upload/defaultProduct.jpg" class="productImg"></label>
                          <label>商品：<input type="text" value="javascript:;"></label>
                          <label>优惠券ID：<input type="text"></label>
                          <input type="button"  value="上传" class="upBtn" />
                          <input type="file" accept="image/gif,image/jpeg,image/jpg,image/png" class="fileProduct">
                          </div>
                      </div>
                      <div class="list">
                        <img src="../../assets/defaultProduct.jpg" />
                        <div class="site">
                          <label>图片：<input type="text" value="http://www.yijiago.com/promotion/app/rearEnd/mall/upload/defaultProduct.jpg" class="productImg"></label>
                          <label>商品：<input type="text" value="javascript:;"></label>
                          <label>优惠券ID：<input type="text"></label>
                          <input type="button"  value="上传" class="upBtn" />
                          <input type="file" accept="image/gif,image/jpeg,image/jpg,image/png" class="fileProduct">
                          </div>
                      </div>
                    </div>
                    <a href="javascript:;" class="delPor">删除</a>
                  </div>
                  <div class="cList timeWrap" v-if="typeTemplat == 'timing'">
                    <ul>
                      <li><span>日期：</span><input type="date" class="startDate">——<input type="date" class="endDate"></li>
                      <li><span>商品ID：</span><input type="text" class="proId"></li>
                      <li><span>商品价格：</span><input type="text" class="price"></li>
                    </ul>
                    <a href="javascript:;" class="delPor">删除</a>
                  </div>
                </div>
                <div class="proWrap" ref="proWrap"></div>
              </div> 
            </li>
            <li><span>代码：</span><textarea class="createCode" ref="createCode"></textarea></li>
        </ul>
        <div class="btnWrap">
            <input type="button"  value="生成代码" @click="getCode()" />
            <a href="javascript:;" class="run" @click='createHtml()'>浏览</a>
            <input type="reset"  value="重置"  />
        </div>
    </form>
  </div>
</template>

<script>
import {codeBuilder} from './codeBuilderJs'

codeBuilder.components = {}

export default codeBuilder

</script>

<style scoped>
@import "codeBuilderCss.css";
</style>
