{{ header }}{{ column_left }}
<div id="content">
  <div class="page-header">
    <div class="container-fluid">
      <div class="pull-right"><!-- <a href="{{ invoice }}" target="_blank" data-toggle="tooltip" title="{{ button_invoice_print }}" class="btn btn-info"><i class="fa fa-print"></i></a> <a href="{{ shipping }}" target="_blank" data-toggle="tooltip" title="{{ button_shipping_print }}" class="btn btn-info"><i class="fa fa-truck"></i></a> --> <!-- <a href="{{ edit }}" data-toggle="tooltip" title="{{ button_edit }}" class="btn btn-primary"><i class="fa fa-pencil"></i></a> --> <a href="{{ cancel }}" data-toggle="tooltip" title="{{ button_cancel }}" class="btn btn-default"><i class="fa fa-reply"></i></a></div>
      <h1>{{ heading_title }}</h1>
      <ul class="breadcrumb">
        {% for breadcrumb in breadcrumbs %}
        <li><a href="{{ breadcrumb.href }}">{{ breadcrumb.text }}</a></li>
        {% endfor %}
      </ul>
    </div>
  </div>
  <div class="container-fluid">
    <div class="row">
      <div class="col-md-6">
        <div class="panel panel-default">
          <div class="panel-heading">
            <h3 class="panel-title"><i class="fa fa-shopping-cart"></i> {{ text_order_detail }}</h3>
          </div>
          <table class="table">
            <tbody>
              <tr>
                <td style="width: 1%;"><button data-toggle="tooltip" title="{{ text_store }}" class="btn btn-info btn-xs"><i class="fa fa-shopping-cart fa-fw"></i></button></td>
                <td>{{ store_name }}</td>
              </tr>
              <tr>
                <td><button data-toggle="tooltip" title="{{ text_date_added }}" class="btn btn-info btn-xs"><i class="fa fa-calendar fa-fw"></i></button></td>
                <td>{{ date_added }}</td><!--订单的生成日期-->
              </tr>
              <tr>
                <td><button data-toggle="tooltip" title="{{ text_payment_method }}" class="btn btn-info btn-xs"><i class="fa fa-credit-card fa-fw"></i></button></td>
                <td>{{ payment_method }}</td>
              </tr>
            {% if shipping_method %}
            <tr>
              <td><button data-toggle="tooltip" title="{{ text_shipping_method }}" class="btn btn-info btn-xs"><i class="fa fa-truck fa-fw"></i></button></td>
              <td>{{ shipping_method }}</td>
            </tr>
            {% endif %}
              </tbody>
            
          </table>
        </div>
      </div>
      <div class="col-md-6">
        <div class="panel panel-default">
          <div class="panel-heading">
            <h3 class="panel-title"><i class="fa fa-user"></i> {{ text_customer_detail }}</h3>
          </div>
          <table class="table">
            <tr>
              <td style="width: 1%;"><button data-toggle="tooltip" title="{{ text_customer }}" class="btn btn-info btn-xs"><i class="fa fa-user fa-fw"></i></button></td>
              <td>{% if customer %} <a href="{{ customer }}" target="_blank">{{ firstname }} {{ lastname }}</a> {% else %}
                {{ firstname }} {{ lastname }}
                {% endif %}</td>
            </tr>
            <tr>
              <td><button data-toggle="tooltip" title="{{ text_customer_group }}" class="btn btn-info btn-xs"><i class="fa fa-group fa-fw"></i></button></td>
              <td>{{ customer_group }}</td>
            </tr>
            <tr>
              <td><button data-toggle="tooltip" title="{{ text_email }}" class="btn btn-info btn-xs"><i class="fa fa-envelope-o fa-fw"></i></button></td>
              <td><a href="mailto:{{ email }}">{{ email }}</a></td>
            </tr>
            <tr>
              <td><button data-toggle="tooltip" title="{{ text_telephone }}" class="btn btn-info btn-xs"><i class="fa fa-phone fa-fw"></i></button></td>
              <td>{{ telephone }}</td>
            </tr>
          </table>
        </div>
      </div>
      <!-- <div class="col-md-4">
        <div class="panel panel-default">
          <div class="panel-heading">
            <h3 class="panel-title"><i class="fa fa-cog"></i> {{ text_option }}</h3>
          </div>
          <table class="table">
            <tbody>
              <tr>
                <td>{{ text_invoice }}</td>
                <td id="invoice" class="text-right">{{ invoice_no }}</td>
                <td style="width: 1%;" class="text-center">{% if not invoice_no %}
                  <button id="button-invoice" data-loading-text="{{ text_loading }}" data-toggle="tooltip" title="{{ button_generate }}" class="btn btn-success btn-xs"><i class="fa fa-cog"></i></button>
                  {% else %}
                  <button disabled="disabled" class="btn btn-success btn-xs"><i class="fa fa-refresh"></i></button>
                  {% endif %}</td>
              </tr>
              <tr>
                <td>{{ text_reward }}</td>
                <td class="text-right">{{ reward }}</td>
                <td class="text-center">{% if customer and reward %}
                  {% if not reward_total %}
                  <button id="button-reward-add" data-loading-text="{{ text_loading }}" data-toggle="tooltip" title="{{ button_reward_add }}" class="btn btn-success btn-xs"><i class="fa fa-plus-circle"></i></button>
                  {% else %}
                  <button id="button-reward-remove" data-loading-text="{{ text_loading }}" data-toggle="tooltip" title="{{ button_reward_remove }}" class="btn btn-danger btn-xs"><i class="fa fa-minus-circle"></i></button>
                  {% endif %}
                  {% else %}
                  <button disabled="disabled" class="btn btn-success btn-xs"><i class="fa fa-plus-circle"></i></button>
                  {% endif %}</td>
              </tr>
              <tr>
                <td>{{ text_affiliate }}
                  {% if affiliate %}
                  (<a href="{{ affiliate }}">{{ affiliate_firstname }} {{ affiliate_lastname }}</a>)
                  {% endif %}</td>
                <td class="text-right">{{ commission }}</td>
                <td class="text-center">{% if affiliate %}
                  {% if not commission_total %}
                  <button id="button-commission-add" data-loading-text="{{ text_loading }}" data-toggle="tooltip" title="{{ button_commission_add }}" class="btn btn-success btn-xs"><i class="fa fa-plus-circle"></i></button>
                  {% else %}
                  <button id="button-commission-remove" data-loading-text="{{ text_loading }}" data-toggle="tooltip" title="{{ button_commission_remove }}" class="btn btn-danger btn-xs"><i class="fa fa-minus-circle"></i></button>
                  {% endif %}
                  {% else %}
                  <button disabled="disabled" class="btn btn-success btn-xs"><i class="fa fa-plus-circle"></i></button>
                  {% endif %}</td>
              </tr>
            </tbody>
          </table>
        </div>
      </div> -->
    </div>
    {# 订单信息 #} 订单信息
    <div class="panel panel-default">
      <div class="panel-heading">
        <h3 class="panel-title"><i class="fa fa-info-circle"></i> {{ text_order }}</h3>
      </div>
      <div class="panel-body">
         {% if pickup == false %}
        <table class="table table-bordered">
          <thead>
            <tr>
              <td style="width: 50%;" class="text-left">{{ text_shipping_address }}</td>
            </tr>
          </thead>
          <tbody>
            <tr>
              <td class="text-left">{{ payment_address }}</td>
              <!-- {% if shipping_method %}
              <td class="text-left">{{ shipping_address }}</td>
              {% endif %} </tr> -->
          </tbody>
        </table>
          {% endif %}
        <table class="table table-bordered">
          <thead>
            <tr>
              <td class="text-left">{{ column_product }}</td>
              <td class="text-left">{{ column_model }}</td>
              <td class="text-right">{{ column_quantity }}</td>
              <td class="text-right">{{ column_price }}</td>
              <td class="text-right">{{ column_total }}</td>
            </tr>
          </thead>
          <tbody>
          
          {% for product in products %}
          <tr>
            <td class="text-left"><a href="{{ product.href }}">{{ product.name }}</a> {% for option in product.option %} <br />
              {% if option.type != 'file' %}
              &nbsp;<small> - {{ option.name }}: {{ option.value }}</small> {% else %}
              &nbsp;<small> - {{ option.name }}: <a href="{{ option.href }}">{{ option.value }}</a></small> {% endif %}
              {% endfor %}</td>
            <td class="text-left">{{ product.model }}</td>
            <td class="text-right">{{ product.quantity }}</td>
            <td class="text-right">{{ product.price }}</td>
            <td class="text-right">{{ product.total }}</td>
          </tr>
          {% endfor %}
          {% for voucher in vouchers %}
          <tr>
            <td class="text-left"><a href="{{ voucher.href }}">{{ voucher.description }}</a></td>
            <td class="text-left"></td>
            <td class="text-right">1</td>
            <td class="text-right">{{ voucher.amount }}</td>
            <td class="text-right">{{ voucher.amount }}</td>
          </tr>
          {% endfor %}
          {% for total in totals %}
          <tr>
            <td colspan="4" class="text-right">{{ total.title }}</td>
            <td class="text-right">{{ total.text }}</td>
          </tr>
          {% endfor %}
            </tbody>
          
        </table>
        {% if comment %}
        <table class="table table-bordered">
          <thead>
            <tr>
              <td>{{ text_comment }}</td>
            </tr>
          </thead>
          <tbody>
            <tr>
              <td>{{ comment }}</td>
            </tr>
          </tbody>
        </table>
        {% endif %} </div>
    </div>

    {# 买家自提信息 #}
    {% if pickup %}
      <div class="panel panel-default">
        <div class="panel-heading">
          <h3 class="panel-title"><i class="fa fa-info-circle"></i> 买家自提信息 </h3>
        </div>
        <div class="panel-body">
          <table class="table table-bordered">
            <thead>
            <tr>
              <td style="width: 50%;" class="text-left"> 自提信息 </td>
            </tr>
            </thead>
            <tbody>
            <tr>
              <td class="text-left"><span>姓名 : </span><span>{{ customer_pickup_name }}</span></td>
            <tr>
            <tr>
              <td class="text-left"><span>电话 : </span><span>{{ customer_pickup_mobile }}</span></td>
            </tr>
            {#<tr>#}
              {#<td class="text-left"><span>备注:</span><span></span></td>#}
            {#</tr>#}
            </tbody>
          </table>
      </div>
      </div>
    {% endif %}

    {# 订单历史记录 #}
    {% if pickup %}
       {# 关闭其他 #}
        <div class="panel panel-default">
            <div class="panel-heading">
                <h3 class="panel-title"><i class="fa fa-comment-o"></i> {{ text_history }}</h3>
            </div>
            <div class="panel-body">
                <div class="tab-content">
                    <div class="tab-pane active" id="tab-history">
                        <div id="history"></div>
                        <br />
                        <fieldset>
                            <legend>{{ text_history_add }}</legend>
                            <div class="tab-pane" id="tab-express">
                                <form class="form-horizontal">
                                    <div class="form-group">
                                        <label class="col-sm-2 control-label" for="input-order-status">{{ entry_order_status }}</label>
                                        <div class="col-sm-10">
                                            <label id="order-status-name" class="control-label" style="font-size: 14px;font-weight: bold;color: #9a2516">{{ order_status }}</label>
                                        </div>
                                    </div>
                                    <!--物流信息模块-->
                                    <div class="form-group">
                                        <label class="col-sm-2 control-label" for="input-comment">{{ entry_comment }}</label>
                                        <div class="col-sm-10">
                                            <textarea name="comment" rows="8" id="input-comment" class="form-control"></textarea>
                                        </div>
                                    </div>
                                    {% if order_status_id == 2 %}
                                        <div class="text-right" id="charge-off">
                                            <button data-loading-text="{{ text_loading }}" class="btn btn-primary" onclick="sendValue($(this).siblings('input').val())" data-toggle="modal" data-target="#myModal" type="button"><i class="fa fa-plus-circle"></i>点击核销</button>
                                            <input type="hidden" value="5" name="pickup-order" >
                                        </div>
                                    {% elseif order_status_id == 1 %}
                                        <div class="text-right" id="charge-cancel">
                                            <button data-loading-text="{{ text_loading }}" class="btn btn-primary" onclick="sendValue($(this).siblings('input').val())" data-toggle="modal" data-target="#myModal" type="button"><i class="fa fa-plus-circle"></i>关闭订单</button>
                                            <input type="hidden" value="7"  name="pickup-order" >
                                        </div>
                                    {% endif %}
                                </form>
                            </div>
                        </fieldset>
                        <!-- 模态框（Modal） -->
                        <div class="modal fade" id="myModal" tabindex="-1" role="dialog" aria-labelledby="myModalLabel" aria-hidden="true">
                            <div class="modal-dialog">
                                <div class="modal-content">
                                    <div class="modal-header">
                                        <button type="button" class="close" data-dismiss="modal" aria-hidden="true">
                                            &times;
                                        </button>
                                        <h4 class="modal-title" id="myModalLabel">
                                            处理订单
                                        </h4>
                                    </div>
                                    <div class="modal-body">
                                        您确定处理此订单吗？
                                    </div>
                                    <div class="modal-footer">
                                        <button type="button" class="btn btn-default" data-dismiss="modal">取消
                                        </button>
                                        <button id="pickup-history"  type="button" class="btn btn-primary" data-dismiss="modal">
                                            <input type="hidden" id="send-value" value="">
                                            确定处理
                                        </button>
                                    </div>
                                </div>
                            </div>
                        </div>
                        <!-- 模态框（Modal）end -->




                    </div>
                </div>
            </div>
        </div>
    {% elseif takeout %}
        {# 同城配送,关闭快递模块 #}
        <div class="panel panel-default">
            <div class="panel-heading">
                <h3 class="panel-title"><i class="fa fa-comment-o"></i> {{ text_history }}</h3>
            </div>
            <div class="panel-body">
                <div class="tab-content">
                    <div class="tab-pane active" id="tab-history">
                        <div id="history"></div>
                        <br />
                        <fieldset>
                            <legend>{{ text_history_add }}</legend>
                            <div class="panel-body">
                                <table class="table table-bordered">
                                    <thead>
                                        <tr>
                                            <td style="width: 50%;" class="text-left"> 订单状态 : <span style="font-size: 14px;font-weight: bold;color: #9a2516">{{ order_status }}</span> </td>
                                        </tr>
                                    </thead>
                                </table>
                            </div>
                            <ul class="nav-tabs nav">
                                <li class="active"><a href="#tab-takeout" data-toggle="tab">第三方配送</a></li>
                                <li><a href="#tab-no_express" data-toggle="tab">无需物流</a></li>
                            </ul>
                            <div class="tab-content">
                                <div class="tab-pane active" id="tab-takeout">
                                    <form class="form-horizontal">
                                        <div class="form-group required">
                                            <label class="col-sm-2 control-label" for="input-override">配送公司</label>
                                            <div class="col-sm-10">
                                                <select class="form-control" name="channel">
                                                    <option value="0"> 请选择同城快递公司</option>
                                                    {% for server in servers %}
                                                        <option value="{{ server.id }}">{{ server.name }}</option>
                                                    {% endfor %}
                                                </select>
                                                <div class="text-dangers"></div>
                                            </div>
                                        </div>
                                        <div class="form-group form_pack_weight required">
                                            <label class="col-sm-2 control-label" for="input-override">配送重量</label>
                                            <div class="col-sm-10">
                                                <label class="radio-inline">
                                                    <input type="radio" name="weight_type" value="1" checked="checked" />
                                                    5千克以内
                                                </label>
                                                <label class="radio-inline">
                                                    <input type="radio" name="weight_type" value="0" />
                                                    <input type="text" name="pack_weight" class="form-control" style="width: 80px;display:inline-block;">千克
                                                </label>
                                                <div class="text-dangers"></div>
                                            </div>
                                        </div>
                                        <div class="form-group ">
                                            <label class="col-sm-2 control-label" for="input-override">配送价格</label>
                                            <div class="col-sm-10">
                                                <input type="text" name="pack_price" class="form-control" style="width: 80px;display:inline-block;" readonly="readonly">元
                                            </div>
                                        </div>
                                        <div class="text-right">
                                            <button  class="btn btn-primary" data-toggle="modal"  type="button" id="js-call-dis"><i class="fa fa-plus-circle"></i> 呼叫配送员</button>
                                        </div>
                                    </form>
                                </div>

                                <div class="tab-pane" id="tab-no_express">
                                    <form class="form-horizontal">
                                        <div class="form-group">
                                            <label class="col-sm-2 control-label" for="input-override">配送说明</label>
                                            <div class="col-sm-10 control-label" style="text-align: left;">
                                                <span clas>点击确定,要自行进行配送</span>
                                            </div>
                                        </div>
                                    </form>
                                    <div class="text-right">
                                        <button  class="btn btn-primary" data-toggle="modal"  type="button" data-target="#confirmSelfSend"><i class="fa fa-plus-circle" ></i>确定</button>
                                    </div>
                                </div>
                            </div>

                        </fieldset>


                        <!-- 模态框（Modal） -->
                        <div class="modal fade" id="confirmSelfSend" tabindex="-1" role="dialog" aria-labelledby="myModalLabel" aria-hidden="true">
                            <div class="modal-dialog">
                                <div class="modal-content">
                                    <div class="modal-header">
                                        <button type="button" class="close" data-dismiss="modal" aria-hidden="true">
                                            &times;
                                        </button>
                                        <h4 class="modal-title" id="myModalLabel">
                                            处理订单
                                        </h4>
                                    </div>
                                    <div class="modal-body">
                                        您确定要自己进行配送么？
                                    </div>
                                    <div class="modal-footer">
                                        <button type="button" class="btn btn-default" data-dismiss="modal">取消
                                        </button>
                                        <button id="button-self" type="button" class="btn btn-primary" data-dismiss="modal">
                                            确定处理
                                        </button>
                                    </div>
                                </div>
                            </div>
                        </div>
                        <!-- 模态框（Modal）end -->

                    </div>
                    <div class="tab-pane" id="tab-additional"> {% if account_custom_fields %}
                            <div class="table-responsive">
                                <table class="table table-bordered">
                                    <thead>
                                    <tr>
                                        <td colspan="2">{{ text_account_custom_field }}</td>
                                    </tr>
                                    </thead>
                                    <tbody>

                                    {% for custom_field in account_custom_fields %}
                                        <tr>
                                            <td>{{ custom_field.name }}</td>
                                            <td>{{ custom_field.value }}</td>
                                        </tr>
                                    {% endfor %}
                                    </tbody>

                                </table>
                            </div>
                        {% endif %}
                        {% if payment_custom_fields %}
                            <div class="table-responsive">
                                <table class="table table-bordered">
                                    <thead>
                                    <tr>
                                        <td colspan="2">{{ text_payment_custom_field }}</td>
                                    </tr>
                                    </thead>
                                    <tbody>

                                    {% for custom_field in payment_custom_fields %}
                                        <tr>
                                            <td>{{ custom_field.name }}</td>
                                            <td>{{ custom_field.value }}</td>
                                        </tr>
                                    {% endfor %}
                                    </tbody>

                                </table>
                            </div>
                        {% endif %}
                        {% if shipping_method and shipping_custom_fields %}
                            <div class="table-responsive">
                                <table class="table table-bordered">
                                    <thead>
                                    <tr>
                                        <td colspan="2">{{ text_shipping_custom_field }}</td>
                                    </tr>
                                    </thead>
                                    <tbody>

                                    {% for custom_field in shipping_custom_fields %}
                                        <tr>
                                            <td>{{ custom_field.name }}</td>
                                            <td>{{ custom_field.value }}</td>
                                        </tr>
                                    {% endfor %}
                                    </tbody>

                                </table>
                            </div>
                        {% endif %}
                        <div class="table-responsive">
                            <table class="table table-bordered">
                                <thead>
                                <tr>
                                    <td colspan="2">{{ text_browser }}</td>
                                </tr>
                                </thead>
                                <tbody>
                                <tr>
                                    <td>{{ text_ip }}</td>
                                    <td>{{ ip }}</td>
                                </tr>
                                {% if forwarded_ip %}
                                    <tr>
                                        <td>{{ text_forwarded_ip }}</td>
                                        <td>{{ forwarded_ip }}</td>
                                    </tr>
                                {% endif %}
                                <tr>
                                    <td>{{ text_user_agent }}</td>
                                    <td>{{ user_agent }}</td>
                                </tr>
                                <tr>
                                    <td>{{ text_accept_language }}</td>
                                    <td>{{ accept_language }}</td>
                                </tr>
                                </tbody>

                            </table>
                        </div>
                    </div>
                    {% for tab in tabs %}
                        <div class="tab-pane" id="tab-{{ tab.code }}">{{ tab.content }}</div>
                    {% endfor %} </div>
            </div>
        </div>
    {% else %}
      {# 关闭同城配送模块 #}
    <div class="panel panel-default">
      <div class="panel-heading">
        <h3 class="panel-title"><i class="fa fa-comment-o"></i>{{ text_history }}</h3>
      </div>
      <div class="panel-body">
        <!-- <ul class="nav nav-tabs">
          <li class="active"><a href="#tab-history" data-toggle="tab">{{ tab_history }}</a></li>
          <li><a href="#tab-additional" data-toggle="tab">{{ tab_additional }}</a></li>
          {% for tab in tabs %}
          <li><a href="#tab-{{ tab.code }}" data-toggle="tab">{{ tab.title }}</a></li>
          {% endfor %}
        </ul> -->
        <div class="tab-content">
          <div class="tab-pane active" id="tab-history">
            <div id="history"></div>
            <br />
            <fieldset>
              <legend>{{ text_history_add }}</legend>
              <ul class="nav-tabs nav">
                <li class="active"><a href="#tab-takeout" data-toggle="tab">第三方配送</a></li>
                <li><a href="#tab-express" data-toggle="tab">物流发货</a></li>
                <li><a href="#tab-no_express" data-toggle="tab">无需物流</a></li>
              </ul>
              <div class="tab-content">
                <div class="tab-pane active" id="tab-takeout">
                  <form class="form-horizontal">
                    <div class="form-group required">
                      <label class="col-sm-2 control-label" for="input-override">配送公司</label>
                      <div class="col-sm-10">
                        <select class="form-control" name="channel">
                          <option value="0">达达</option>
                        </select>
                        <div class="text-dangers"></div>
                      </div>
                    </div>
                    <div class="form-group form_pack_weight required">
                      <label class="col-sm-2 control-label" for="input-override">配送重量</label>
                      <div class="col-sm-10">
                        <label class="radio-inline">
                          <input type="radio" name="weight_type" value="1" checked="checked" />
                          5千克以内
                        </label>
                        <label class="radio-inline">
                          <input type="radio" name="weight_type" value="0" />
                          <input type="text" name="pack_weight" class="form-control" style="width: 80px;display:inline-block;">千克
                        </label>
                        <div class="text-dangers"></div>
                      </div>
                    </div>
                    <div class="form-group">
                      <label class="col-sm-2 control-label" for="input-override">配送价格</label>
                      <div class="col-sm-10">
                          <input type="text" name="pack_price" class="form-control" style="width: 80px;display:inline-block;" readonly="readonly">元
                      </div>
                    </div>
                    <div class="text-right">
                        <button  class="btn btn-primary" data-toggle="modal"  type="button" id="js-call-dis"><i class="fa fa-plus-circle"></i> 呼叫配送员</button>
                      </div>
                  </form>
                </div>
                <div class="tab-pane" id="tab-express">
                    <form class="form-horizontal">
                      <div class="form-group">
                        <label class="col-sm-2 control-label" for="input-order-status">{{ entry_order_status }}</label>
                        <div class="col-sm-10">
                          <select name="order_status_id" id="input-order-status" class="form-control">
                            {% for order_statuses in order_statuses %}
                            {% if order_statuses.order_status_id == order_status_id %}
                            <option value="{{ order_statuses.order_status_id }}" selected="selected">{{ order_statuses.name }}</option>
                            {% else %}
                            <option value="{{ order_statuses.order_status_id }}">{{ order_statuses.name }}</option>
                            {% endif %}
                            {% endfor %}
                          </select>
                        </div>
                      </div>
                      <!--物流信息模块-->
                        <div class="form-group">
                          <label class="col-sm-2 control-label" for="input-override"><span data-toggle="tooltip" title="添加快递公司">快递公司</span></label>
                          <div class="col-sm-4">
                            <select class="form-control" name="shipping_abbr" id="order-shipping-abbr">
                              <option value="">请选择物流公司</option>
                              {% for key,value in shipping_info %}
                              <option value="{{ key }}" {% if key == order_shipping_abbr %} selected {% endif %}>{{ value }}</option>
                              {% endfor %}
                            </select>
                          </div>
                          <label class="col-sm-2 control-label" for="input-override"><span data-toggle="tooltip" title="添加物流单号">物流单号</span></label>

                          <div class="col-sm-4">
                            {% if order_shipping_no %}
                              <input type="text" class="form-control" name="shipping-no" value="{{ order_shipping_no }}"  id="order-shipping-no" />
                            {% else %}
                              <input type="text" class="form-control" name="shipping-no" value="0"  id="order-shipping-no" />
                            {% endif %}
                          </div>
                        </div>

                      <!--物流信息结束-->
                       覆盖
                      <!-- <div class="form-group">
                        <label class="col-sm-2 control-label" for="input-override"><span data-toggle="tooltip" title="{{ help_override }}">{{ entry_override }}</span></label>
                        <div class="col-sm-10">
                          <div class="checkbox">
                            <input type="checkbox" name="override" value="1" id="input-override" />
                          </div>
                        </div>
                      </div>
 -->                       提示会员
                      <div class="form-group">
                        <label class="col-sm-2 control-label" for="input-notify">{{ entry_notify }}</label>
                        <div class="col-sm-10">
                          <div class="checkbox">
                            <input type="checkbox" name="notify" value="1" id="input-notify" />
                          </div>
                        </div>
                      </div>

                      <div class="form-group">
                        <label class="col-sm-2 control-label" for="input-comment">{{ entry_comment }}</label>
                        <div class="col-sm-10">
                          <textarea name="comment" rows="8" id="input-comment" class="form-control"></textarea>
                        </div>
                      </div>
                      <div class="text-right">
                        <button data-loading-text="{{ text_loading }}" class="btn btn-primary" data-toggle="modal" data-target="#myModal" type="button"><i class="fa fa-plus-circle"></i> {{ button_history_add }}</button>
                      </div>
                    </form>
                </div>
                <div class="tab-pane" id="tab-no_express">
                  <div class="text-right">
                        <button  class="btn btn-primary" data-toggle="modal"  type="button"><i class="fa fa-plus-circle"></i>确定</button>
                      </div>
                </div>
              </div>

            </fieldset>


            <!-- 模态框（Modal） -->
            <div class="modal fade" id="myModal" tabindex="-1" role="dialog" aria-labelledby="myModalLabel" aria-hidden="true">
              <div class="modal-dialog">
                <div class="modal-content">
                  <div class="modal-header">
                    <button type="button" class="close" data-dismiss="modal" aria-hidden="true">
                      &times;
                    </button>
                    <h4 class="modal-title" id="myModalLabel">
                      处理订单
                    </h4>
                  </div>
                  <div class="modal-body">
                    您确定处理此订单吗？
                  </div>
                  <div class="modal-footer">
                    <button type="button" class="btn btn-default" data-dismiss="modal">取消
                    </button>
                    <button id="button-history" type="button" class="btn btn-primary" data-dismiss="modal">
                      确定处理
                    </button>
                  </div>
                </div>
              </div>
            </div>
            <!-- 模态框（Modal）end -->

          </div>
          <div class="tab-pane" id="tab-additional"> {% if account_custom_fields %}
            <div class="table-responsive">
              <table class="table table-bordered">
                <thead>
                  <tr>
                    <td colspan="2">{{ text_account_custom_field }}</td>
                  </tr>
                </thead>
                <tbody>

                {% for custom_field in account_custom_fields %}
                <tr>
                  <td>{{ custom_field.name }}</td>
                  <td>{{ custom_field.value }}</td>
                </tr>
                {% endfor %}
                  </tbody>

              </table>
            </div>
            {% endif %}
            {% if payment_custom_fields %}
            <div class="table-responsive">
              <table class="table table-bordered">
                <thead>
                  <tr>
                    <td colspan="2">{{ text_payment_custom_field }}</td>
                  </tr>
                </thead>
                <tbody>

                {% for custom_field in payment_custom_fields %}
                <tr>
                  <td>{{ custom_field.name }}</td>
                  <td>{{ custom_field.value }}</td>
                </tr>
                {% endfor %}
                  </tbody>

              </table>
            </div>
            {% endif %}
            {% if shipping_method and shipping_custom_fields %}
            <div class="table-responsive">
              <table class="table table-bordered">
                <thead>
                  <tr>
                    <td colspan="2">{{ text_shipping_custom_field }}</td>
                  </tr>
                </thead>
                <tbody>

                {% for custom_field in shipping_custom_fields %}
                <tr>
                  <td>{{ custom_field.name }}</td>
                  <td>{{ custom_field.value }}</td>
                </tr>
                {% endfor %}
                  </tbody>

              </table>
            </div>
            {% endif %}
            <div class="table-responsive">
              <table class="table table-bordered">
                <thead>
                  <tr>
                    <td colspan="2">{{ text_browser }}</td>
                  </tr>
                </thead>
                <tbody>
                  <tr>
                    <td>{{ text_ip }}</td>
                    <td>{{ ip }}</td>
                  </tr>
                {% if forwarded_ip %}
                <tr>
                  <td>{{ text_forwarded_ip }}</td>
                  <td>{{ forwarded_ip }}</td>
                </tr>
                {% endif %}
                <tr>
                  <td>{{ text_user_agent }}</td>
                  <td>{{ user_agent }}</td>
                </tr>
                <tr>
                  <td>{{ text_accept_language }}</td>
                  <td>{{ accept_language }}</td>
                </tr>
                  </tbody>

              </table>
            </div>
          </div>
          {% for tab in tabs %}
          <div class="tab-pane" id="tab-{{ tab.code }}">{{ tab.content }}</div>
          {% endfor %} </div>
      </div>
    </div>
    {% endif %}
  </div>
<script type="text/javascript">
  $(document).delegate('#button-invoice', 'click', function() {
  	$.ajax({
  		url: 'index.php?route=sale/order/createinvoiceno&user_token={{ user_token }}&order_id={{ order_id }}',
  		dataType: 'json',
  		beforeSend: function() {
  			$('#button-invoice').button('loading');
  		},
  		complete: function() {
  			$('#button-invoice').button('reset');
  		},
  		success: function(json) {
  			$('.alert-dismissible').remove();

  			if (json['error']) {
  				$('#content > .container-fluid').prepend('<div class="alert alert-danger alert-dismissible"><i class="fa fa-exclamation-circle"></i> ' + json['error'] + '</div>');
  			}

  			if (json['invoice_no']) {
  				$('#invoice').html(json['invoice_no']);

  				$('#button-invoice').replaceWith('<button disabled="disabled" class="btn btn-success btn-xs"><i class="fa fa-cog"></i></button>');
  			}
  		},
  		error: function(xhr, ajaxOptions, thrownError) {
  			alert(thrownError + "\r\n" + xhr.statusText + "\r\n" + xhr.responseText);
  		}
  	});
  });

  $(document).delegate('#button-reward-add', 'click', function() {
  	$.ajax({
  		url: 'index.php?route=sale/order/addreward&user_token={{ user_token }}&order_id={{ order_id }}',
  		type: 'post',
  		dataType: 'json',
  		beforeSend: function() {
  			$('#button-reward-add').button('loading');
  		},
  		complete: function() {
  			$('#button-reward-add').button('reset');
  		},
  		success: function(json) {
  			$('.alert-dismissible').remove();

  			if (json['error']) {
  				$('#content > .container-fluid').prepend('<div class="alert alert-danger alert-dismissible"><i class="fa fa-exclamation-circle"></i> ' + json['error'] + '</div>');
  			}

  			if (json['success']) {
                  $('#content > .container-fluid').prepend('<div class="alert alert-success alert-dismissible"><i class="fa fa-check-circle"></i> ' + json['success'] + '</div>');

  				$('#button-reward-add').replaceWith('<button id="button-reward-remove" data-toggle="tooltip" title="{{ button_reward_remove }}" class="btn btn-danger btn-xs"><i class="fa fa-minus-circle"></i></button>');
  			}
  		},
  		error: function(xhr, ajaxOptions, thrownError) {
  			alert(thrownError + "\r\n" + xhr.statusText + "\r\n" + xhr.responseText);
  		}
  	});
  });

  $(document).delegate('#button-reward-remove', 'click', function() {
  	$.ajax({
  		url: 'index.php?route=sale/order/removereward&user_token={{ user_token }}&order_id={{ order_id }}',
  		type: 'post',
  		dataType: 'json',
  		beforeSend: function() {
  			$('#button-reward-remove').button('loading');
  		},
  		complete: function() {
  			$('#button-reward-remove').button('reset');
  		},
  		success: function(json) {
  			$('.alert-dismissible').remove();

  			if (json['error']) {
  				$('#content > .container-fluid').prepend('<div class="alert alert-danger alert-dismissible"><i class="fa fa-exclamation-circle"></i> ' + json['error'] + '</div>');
  			}

  			if (json['success']) {
                  $('#content > .container-fluid').prepend('<div class="alert alert-success alert-dismissible"><i class="fa fa-check-circle"></i> ' + json['success'] + '</div>');

  				$('#button-reward-remove').replaceWith('<button id="button-reward-add" data-toggle="tooltip" title="{{ button_reward_add }}" class="btn btn-success btn-xs"><i class="fa fa-plus-circle"></i></button>');
  			}
  		},
  		error: function(xhr, ajaxOptions, thrownError) {
  			alert(thrownError + "\r\n" + xhr.statusText + "\r\n" + xhr.responseText);
  		}
  	});
  });

  $(document).delegate('#button-commission-add', 'click', function() {
  	$.ajax({
  		url: 'index.php?route=sale/order/addcommission&user_token={{ user_token }}&order_id={{ order_id }}',
  		type: 'post',
  		dataType: 'json',
  		beforeSend: function() {
  			$('#button-commission-add').button('loading');
  		},
  		complete: function() {
  			$('#button-commission-add').button('reset');
  		},
  		success: function(json) {
  			$('.alert-dismissible').remove();

  			if (json['error']) {
  				$('#content > .container-fluid').prepend('<div class="alert alert-danger alert-dismissible"><i class="fa fa-exclamation-circle"></i> ' + json['error'] + '</div>');
  			}

  			if (json['success']) {
                  $('#content > .container-fluid').prepend('<div class="alert alert-success alert-dismissible"><i class="fa fa-check-circle"></i> ' + json['success'] + '</div>');

  				$('#button-commission-add').replaceWith('<button id="button-commission-remove" data-toggle="tooltip" title="{{ button_commission_remove }}" class="btn btn-danger btn-xs"><i class="fa fa-minus-circle"></i></button>');
  			}
  		},
  		error: function(xhr, ajaxOptions, thrownError) {
  			alert(thrownError + "\r\n" + xhr.statusText + "\r\n" + xhr.responseText);
  		}
  	});
  });

  $(document).delegate('#button-commission-remove', 'click', function() {
  	$.ajax({
  		url: 'index.php?route=sale/order/removecommission&user_token={{ user_token }}&order_id={{ order_id }}',
  		type: 'post',
  		dataType: 'json',
  		beforeSend: function() {
  			$('#button-commission-remove').button('loading');
  		},
  		complete: function() {
  			$('#button-commission-remove').button('reset');
  		},
  		success: function(json) {
  			$('.alert-dismissible').remove();

  			if (json['error']) {
  				$('#content > .container-fluid').prepend('<div class="alert alert-danger alert-dismissible"><i class="fa fa-exclamation-circle"></i> ' + json['error'] + '</div>');
  			}

  			if (json['success']) {
                  $('#content > .container-fluid').prepend('<div class="alert alert-success alert-dismissible"><i class="fa fa-check-circle"></i> ' + json['success'] + '</div>');

  				$('#button-commission-remove').replaceWith('<button id="button-commission-add" data-toggle="tooltip" title="{{ button_commission_add }}" class="btn btn-success btn-xs"><i class="fa fa-plus-circle"></i></button>');
  			}
  		},
  		error: function(xhr, ajaxOptions, thrownError) {
  			alert(thrownError + "\r\n" + xhr.statusText + "\r\n" + xhr.responseText);
  		}
  	});
  });

  $('#history').delegate('.pagination a', 'click', function(e) {
  	e.preventDefault();

  	$('#history').load(this.href);
  });

  $('#history').load('index.php?route=sale/order/history&user_token={{ user_token }}&order_id={{ order_id }}');

  $('#button-history').on('click', function() {
   
  	$.ajax({
  		url: '{{ catalog }}index.php?route=api/order/history&api_token={{ api_token }}&store_id={{ store_id }}&order_id={{ order_id }}',
  		type: 'post',
  		dataType: 'json',
  		data: 'order_status_id=' + encodeURIComponent($('select[name=\'order_status_id\']').val()) + '&notify=' + ($('input[name=\'notify\']').prop('checked') ? 1 : 0) + '&override=' + ($('input[name=\'override\']').prop('checked') ? 1 : 0) + '&append=' + ($('input[name=\'append\']').prop('checked') ? 1 : 0) + '&comment=' + encodeURIComponent($('textarea[name=\'comment\']').val()) + '&shipping_no='+($('input[name=\'shipping-no\']').val()) + '&shipping_abbr='+($('select[name=\'shipping_abbr\'] option:selected').val()),
  		beforeSend: function() {
  			$('#button-history').button('loading');
  		},
  		complete: function() {
  			$('#button-history').button('reset');
  		},
  		success: function(json) {
  			$('.alert-dismissible').remove();

  			if (json['error']) {
  				$('#history').before('<div class="alert alert-danger alert-dismissible"><i class="fa fa-exclamation-circle"></i> ' + json['error'] + ' <button type="button" class="close" data-dismiss="alert">&times;</button></div>');
  			}

  			if (json['success']) {
  				$('#history').load('index.php?route=sale/order/history&user_token={{ user_token }}&order_id={{ order_id }}');

  				$('#history').before('<div class="alert alert-success alert-dismissible"><i class="fa fa-check-circle"></i> ' + json['success'] + ' <button type="button" class="close" data-dismiss="alert">&times;</button></div>');

  				$('textarea[name=\'comment\']').val('');
  				if(json['order_status_id'] == 2){
                      $("#order-shipping-abbr").attr('disabled',false);
                      $("#order-shipping-no").attr('disabled',false)
                  }else{
                      $("#order-shipping-abbr").attr('disabled',true);
                      $("#order-shipping-no").attr('disabled',true)
                  }

  			}
  		},
  		error: function(xhr, ajaxOptions, thrownError) {
  			alert(thrownError + "\r\n" + xhr.statusText + "\r\n" + xhr.responseText);
  		}
  	});
});
</script>
<script type="text/javascript">
  var order_status_id = {{ order_status_id }};
  $(function () {
      if(order_status_id != 2){
          $("#order-shipping-abbr").attr('disabled',true);
          $("#order-shipping-no").attr('disabled',true)
      }

  });
</script>
<script type="text/javascript">
    $('#pickup-history').on('click', function() {
       console.log($("#send-value").val());
        $.ajax({
            url: '{{ catalog }}index.php?route=api/order/pickup&api_token={{ api_token }}&store_id={{ store_id }}&order_id={{ order_id }}',
            type: 'post',
            dataType: 'json',
            data: 'order_status_id=' + encodeURIComponent($("#send-value").val())+'&comment='+encodeURIComponent($('textarea[name=\'comment\']').val()),
            beforeSend: function() {
                $('#pickup-history').button('loading');
            },
            complete: function() {
                $('#pickup-history').button('reset');
            },
            success: function(json) {
                $('.alert-dismissible').remove();

                if (json['error']) {
                    $('#history').before('<div class="alert alert-danger alert-dismissible"><i class="fa fa-exclamation-circle"></i> ' + json['error'] + ' <button type="button" class="close" data-dismiss="alert">&times;</button></div>');
                }

                if (json['success']) {
                    $('#history').load('index.php?route=sale/order/history&user_token={{ user_token }}&order_id={{ order_id }}');

                    $('#history').before('<div class="alert alert-success alert-dismissible"><i class="fa fa-check-circle"></i> ' + json['success'] + ' <button type="button" class="close" data-dismiss="alert">&times;</button></div>');

                    $('textarea[name=\'comment\']').val('');
                    //修改订单状态和隐藏按钮
                    if(json['order_status_id'] == 5){
                        $("#charge-off").css("display",'none');
                        $("#order-status-name").text(json['order_status_name']);
                    }
                    if(json['order_status_id'] == 7){
                        $("#charge-cancel").css("display",'none');
                        $("#order-status-name").text(json['order_status_name']);
                    }

                }
            },
            error: function(xhr, ajaxOptions, thrownError) {
                alert(thrownError + "\r\n" + xhr.statusText + "\r\n" + xhr.responseText);
            }
        });

    });

    function sendValue(val){
        $("#send-value").val(val);
    }
</script>

<script type="text/javascript">
  $("select[name='channel']").change(function(event) {
    /* Act on the event */
    console.log($(this).val())
    if($(this).val() != 0){
      $(this).parents(".form-group.required").removeClass("has-error");
      $(this).parents(".col-sm-10").find(".text-dangers").text('').removeClass('text-danger');
    }
    var weight_type = $("input[name='weight_type']:checked").val();
    console.log(weight_type);
    $.ajax({
      url:"",
      data:{},
      dataType:"JSON",
      success:function(e){

      }
    });
  });
  $("input[name='weight_type']").change(function(){  //单选框选中重量
    console.log($(this).val())
    var weight_type = $(this).val();
    var pack_weight = $("input[name='pack_weight']").val();
    if(weight_type == 0){  // 0需要输入重量
      $(this).siblings("input[name='pack_weight']").focus();
    }
    
    $.ajax({
      url:"",
      data:{},
      dataType:"JSON",
      success:function(e){

      }
    });
  });
  $("input[name='pack_weight']").keyup(function() {
    $(this).val($(this).val().replace(/[^0-9.]/g,''));
    if($(this).val().length > 0){
      $(this).parents(".form-group.required").removeClass("has-error");
      $(this).parents(".col-sm-10").find(".text-dangers").text('').removeClass('text-danger');
    }
  })
  $("#js-call-dis").click(function(){
    var channel = $("select[name='channel'] option:selected").val();
    var weight_type = $("input[name='weight_type']:checked").val();
    var pack_weight = $("input[name='pack_weight']").val();
    console.log(channel)
    console.log(weight_type)
    if(channel == 0){
      $("select[name='channel']").parents(".form-group.required").addClass("has-error");
      $("select[name='channel']").parents(".col-sm-10").find(".text-dangers").text('请选择同城快递公司！').addClass('text-danger');
      return;
    }
    else if(weight_type == 0 && pack_weight <= 0){
      $("input[name='weight_type").parents(".form-group.required").addClass("has-error");
      $("input[name='weight_type']").parents(".col-sm-10").find(".text-dangers").text('请输入配送重量！').addClass('text-danger');
      return;
    }
  });
</script>
</div>
{{ footer }} 