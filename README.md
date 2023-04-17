<%@ Page Title="" Language="C#" MasterPageFile="~/Main.master" AutoEventWireup="true" CodeFile="Listing.aspx.cs" Inherits="Users_Listing" %>




<asp:Content ID="Content2" ContentPlaceHolderID="ContentPlaceHolder1" runat="Server">
    <div class="row">
        <div class="col-md-12">
            <div class="card">
                <div class="card-header header-elements-inline">
                    <div class="col-md-11">
                        <button type="button" class="btn btn-primary" data-toggle="modal" data-target="#modal_form_vertical" onclick="clearData();">Add New Listing</button>
                        <asp:Button runat="server" ID="btnchangestatus" class="btn btn-primary" formnovalidate Text="Change Status" OnClientClick="return confirm('Do You Really Want to Change Status for Selected??')"></asp:Button>
                    </div>
                    <ul class="navbar-nav ml-lg-auto">
                        <li class="nav-item" data-popup="popover" title="" data-trigger="hover" data-html="true"
                            data-content="<ul class='list-extended pl-3'><li></li><li></li><li></li><li></li><li></li></ul>"
                            data-original-title="<h6 class='p-0'>Risk Profile Creation Help</h6>"><a href="#" class="navbar-nav-link  p-0"><i class="icon-info3"></i></a></li>
                    </ul>
                </div>
                <hr style="margin: 0" />
                <div class="card-body p-0">
                    <ul class="nav nav-tabs nav-tabs-highlight mb-0">
                        <li class="nav-item"><a href="#bordered-tab1" class="nav-link active" data-toggle="tab">Active</a></li>
                        <li class="nav-item"><a href="#bordered-tab2" class="nav-link" data-toggle="tab">InActive</a></li>
                    </ul>
                    <div class="tab-content card card-body border-top-0 rounded-top-0 mb-0 p-0">
                        <div class="tab-pane fade show active" id="bordered-tab1">
                            <div class="grid-container">
                                <dx:ASPxGridView ID="dgvbasketactive" runat="server" CssClass="table datatable-basic table-bordered" SettingsPager-PageSize="20" EnableRowsCache="false">
                                    <Settings ShowGroupPanel="true" />
                                    <Settings ShowFilterRow="true" />
                                    <Columns>
                                        <dx:GridViewDataCheckColumn>
                                            <DataItemTemplate>
                                                <dx:ASPxCheckBox ID="gvchk" pid='<%# Eval("ProfileID") %>' status='<%# Eval("ProfileStatus") %>' name='<%# Eval("ProfileName") %>' runat="server" AllowGrayed="false" ValueType="System.Boolean" ValueChecked="true" ValueUnchecked="false" ToolTip='<%# Eval("ProfileID") %>'></dx:ASPxCheckBox>
                                            </DataItemTemplate>
                                        </dx:GridViewDataCheckColumn>
                                        <dx:GridViewDataCheckColumn Caption="Edit">
                                            <DataItemTemplate>
                                                <a data-toggle="modal" data-target="#modal_form_vertical" onclick="setData(this.name)" name='<%# Eval("ProfileName") + "|" + Eval("ProfileDesc") + "|" + Eval("LowRange") + "|" + Eval("HighRange") + "|" + Eval("ProfileID")+ "|" + Eval("Colour") %>' style="cursor: pointer; color: #75aaff" id="lblmodel" runat="server"><i class="icon-pencil5"></i></a>
                                            </DataItemTemplate>
                                        </dx:GridViewDataCheckColumn>
                                        <dx:GridViewDataColumn FieldName="ISIN" />
                                        <dx:GridViewDataColumn FieldName="Share Name" />
                                        <dx:GridViewDataColumn FieldName="Partner Sec ID" />
                                        <dx:GridViewDataColumn FieldName="Partner Price" />
                                        <dx:GridViewDataColumn FieldName="Partner Lot Size" />
                                        <dx:GridViewDataColumn FieldName="Total Qty (in multiples of lotsize)" />
                                        <dx:GridViewDataColumn FieldName="Total Used Qty" />
                                        <dx:GridViewDataColumn FieldName="Status" />
                                        <dx:GridViewDataCheckColumn Caption="Partner ID">
                                            <DataItemTemplate>
                                                <div style='<%# "border:1px solid silver; background-color:" + DataBinder.Eval(Container.DataItem, "Colour") + ";" %>'>&nbsp;</div>
                                            </DataItemTemplate>
                                        </dx:GridViewDataCheckColumn>
                                        <dx:GridViewDataColumn FieldName="Createddate" Caption="Created Date & Time" />
                                        <dx:GridViewDataColumn FieldName="Updateddate" Caption="Updated Date & Time" />
                                    </Columns>
                                </dx:ASPxGridView>
                            </div>
                            </div>
                        <div class="tab-pane fade" id="bordered-tab2">
                            <div class="grid-container" id="grpid">
                                <dx:ASPxGridView ID="dgvbasketInActive" runat="server" CssClass="table datatable-basic table-bordered" SettingsPager-PageSize="20" EnableRowsCache="false">
                                    <Settings ShowGroupPanel="true" />
                                    <Settings ShowFilterRow="true" />
                                    <Columns>
                                        <dx:GridViewDataCheckColumn>
                                            <DataItemTemplate>
                                                <dx:ASPxCheckBox ID="gvchk" pid='<%# Eval("ProfileID") %>' status='<%# Eval("ProfileStatus") %>' name='<%# Eval("ProfileName") %>' runat="server" AllowGrayed="false" ValueType="System.Boolean" ValueChecked="true" ValueUnchecked="false" ToolTip='<%# Eval("ProfileID") %>'></dx:ASPxCheckBox>
                                            </DataItemTemplate>
                                        </dx:GridViewDataCheckColumn>
                                        <dx:GridViewDataCheckColumn Caption="Edit">
                                            <DataItemTemplate>
                                                <a data-toggle="modal" data-target="#modal_form_vertical" onclick="setData(this.name)" name='<%# Eval("ProfileName") + "|" + Eval("ProfileDesc") + "|" + Eval("LowRange") + "|" + Eval("HighRange") + "|" + Eval("ProfileID")+ "|" + Eval("Colour") %>' style="cursor: pointer; color: #75aaff" id="lblmodel" runat="server"><i class="icon-pencil5"></i></a>
                                            </DataItemTemplate>
                                        </dx:GridViewDataCheckColumn>
                                        <dx:GridViewDataColumn FieldName="ISIN" />
                                        <dx:GridViewDataColumn FieldName="Share Name" />
                                        <dx:GridViewDataColumn FieldName="Partner Sec ID" />
                                        <dx:GridViewDataColumn FieldName="Partner Price" />
                                        <dx:GridViewDataColumn FieldName="Partner Lot Size" />
                                        <dx:GridViewDataColumn FieldName="Total Qty (in multiples of lotsize)" />
                                        <dx:GridViewDataColumn FieldName="Total Used Qty" />
                                        <dx:GridViewDataColumn FieldName="Status" />
                                        <dx:GridViewDataCheckColumn Caption="Partner ID">
                                            <DataItemTemplate>
                                                <div style='<%# "border:1px solid silver; background-color:" + DataBinder.Eval(Container.DataItem, "Colour") + ";" %>'>&nbsp;</div>
                                            </DataItemTemplate>
                                        </dx:GridViewDataCheckColumn>
                                        <dx:GridViewDataColumn FieldName="Createddate" Caption="Created Date & Time" />
                                        <dx:GridViewDataColumn FieldName="Updateddate" Caption="Updated Date & Time" />
                                    </Columns>
                                </dx:ASPxGridView>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
            <!-- Create New Profile -->
    <div id="modal_form_vertical" class="modal fade" tabindex="-1" data-backdrop="static" data-keyboard="false">
    <div class="modal-dialog">
        <div class="modal-content">
            <div class="modal-header">
                <h5 class="modal-title">New Listing</h5>
                <button type="button" class="close" data-dismiss="modal">&times;</button>
            </div>
            <div class="modal-body">
                <fieldset id="portfolio" style="border: 1px solid silver; border-radius: 10px; padding: 0px 15px 15px;">
                    <legend class="font-weight-semibold">Add New Listing</legend>
                    <div class="form-group">
                        <div class="row">
                            <div class="col-sm-3">
                                            <asp:RadioButtonList runat="server" Style="margin-top: 1px;" ID="rbl_stock_mf">
                                                <asp:ListItem Selected="True">Fund</asp:ListItem>
                                                <asp:ListItem>Isin</asp:ListItem>
                                            </asp:RadioButtonList>
                                        </div>
                            <div class="col-sm-9">
                                 <label>Symbol/ISIN <span class="red">*</span></label>
                                <asp:TextBox runat="server" ID="txt_symbolsearch" CssClass="form-control" placeholder="Search Symbol"></asp:TextBox>
                           </div>
                        </div>
                    </div>
                  <div class="form-group">
                        <div class="row">
                            <div class="col-sm-6">
                                  <label>Minimum Quantity to Buy <span class="red">*</span></label>
          <asp:TextBox runat="server" ID="txtbx_MinQty" CssClass="form-control" placeholder="Minimum Quantity"></asp:TextBox>
        </div>
        <div class="col-sm-6">
          <label>Quantity <span class="red">*</span></label>
          <asp:TextBox runat="server" ID="txtbx_Qty" CssClass="form-control" placeholder="Quantity"></asp:TextBox>
        </div>
      </div>
    </div>
                    <div class="form-group">
                        <div class="row">
                            <div class="col-sm-12">
                                <label>Partner Price</label>
                                <asp:TextBox runat="server" ID="txtbx_Price" CssClass="form-control" placeholder="Price"></asp:TextBox>
                            </div>
                        </div>
                    </div>
                   <div class="col-sm-5" style="padding-bottom: 25px;">
                            <button class="btn btn-primary" style="padding: 1.5px 10px;" id="btn_add" onclick="AddDetails(); return false;">Add</button>
                                        </div>
                       <div class="form-group  mb-0">
                            <div class="grid-container">
                                <table class="table table-bordered customTable" border="1">
                                    <thead>
                                        <tr class="text-center">
                                            <th>Action</th>
                                            <th>Symbol</th>
                                            <th>IsinCode</th>
                                            <th>SecurityId</th>
                                            <th>Quantity</th>
                                            <th>Price</th>
                                            <th>MinQty</th>
                                            <th>UpdateBy</th>
                                            <th>UpdateId</th>
                                        </tr>
                                    </thead>
                                    <tbody id="scriptData">
                                    </tbody>
                                </table>
                            </div>
                        </div>

                </fieldset>
            </div>
            <div class="modal-footer">
                <asp:Button runat="server" ID="btnsubmit" class="btn bg-primary" Text="Submit"  OnClientClick="return validate()" />
                <button class="btn bg-primary" data-dismiss="modal">Close</button>
            </div>
        </div>
    </div>
</div>

            </div>
        </div>
               <script src="../assets/js/jquery-ui.min.js"></script>
    <script>
        $(function () {
            $("[id$=ContentPlaceHolder1_txt_symbolsearch]").autocomplete({
                source: function (request, response) {
                    $.ajax({
                        url: 'Listing.aspx/symbolSearch',
                        data: "{'type':'" + $("#ContentPlaceHolder1_rbl_stock_mf :checked").val() + "','searchText': '" + request.term + "'}",
                        dataType: "json",
                        type: "POST",
                        contentType: "application/json; charset=utf-8",
                        success: function (data) {
                            response($.map(data.d, function (item) {
                                return { label: item, val: item }
                            }))
                        },
                        error: function (response) {
                            $("#lblmessage").text(response.responseJSON.Message);
                            error();
                        },
                        failure: function (response) {
                            $("#lblmessage").text(response.responseJSON.Message);
                            error();
                        }
                    });
                },
                select: function (e, i) {

                },
                close: function () {

                }
            });
        });


        function AddDetails() {
            if ($("#ContentPlaceHolder1_txt_symbolsearch").val() != ""
                && ($("#ContentPlaceHolder1_txt_price").val() != "" || $("#ContentPlaceHolder1_txt_nos").val() != "")
                ) {

                $.ajax({
                    url: '<%=ResolveUrl("Listing.aspx/AddData") %>',
                    data: "{ 'scripttype':'" + $("#ContentPlaceHolder1_rbl_stock_mf input:checked").val()
                        + "','symbol':'" + $("#ContentPlaceHolder1_txt_symbolsearch").val()
                        + "','price':'" + $("#ContentPlaceHolder1_txt_price").val()
                        + "','minqty':'" + $("#ContentPlaceHolder1_txtbx_MinQty").val()
                        + "','qty':'" + $("#ContentPlaceHolder1_txt_nos").val()
                        + "'}",
                    contentType: "application/json; charset=utf-8",
                    dataType: "json",
                    type: "POST",
                    success: function (data) {

                        if (data.d.includes("Already") == true) {
                            $("#lblmessage").text(data.d);
                            error();
                        }
                        else {
                            BindData(data);
                        }
                        $("#ContentPlaceHolder1_txt_symbolsearch").val("");
                        $("#ContentPlaceHolder1_txt_price").val("");
                        $("#ContentPlaceHolder1_txt_nos").val("");
                        $("#ContentPlaceHolder1_txtbx_MinQty").val("");


                        //$("#ContentPlaceHolder1_txt_secper").val("");
                    },
                    error: function (e) {
                        $("#lblmessage").text("Something went Wrong!!! Please try Again.");
                        error();
                    }
                });
            }
            else {
                $("#lblmessage").text("Please select Script to add.");
                error();
            }
        }

        function BindData(data) {
            var obj = JSON.parse(data.d);
            var list = "";
            for (var i = 0; i < obj.length; i++) {
                list += '<tr><td class="text-center"><a name="' + obj[i].IsinCode + '" onclick="DeleteScriptDetails(this.name); return false;" title="Delete" style="cursor:pointer"><i class="icon-trash" style="color:red"></i></a></td>' +
                    '<td>' + obj[i].Symbol + '</td>' +
                    '<td>' + obj[i].IsinCode + '</td>' +
                    '<td>' + obj[i].secid + '</td>' +
                    '<td class="qty">'+ obj[i].Qty + '</td>' +
                    '<td>' + obj[i].price + '</td>' +
                    '<td>' + obj[i].MinQty + '</td>' +
                    '<td>' + obj[i].UpdatedIP + '</td></tr>';
            }
            $("#scriptData").html(list);
            hideColumns();
        }

    </script>
</asp:Content>

