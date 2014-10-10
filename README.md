UI-work
=======




<script src="//ajax.googleapis.com/ajax/libs/jquery/1.7.2/jquery.min.js"></script>
<script src="//ajax.googleapis.com/ajax/libs/jqueryui/1.8.18/jquery-ui.min.js"></script>


<script language="javascript" type="text/javascript" src="http://gblon-i-dw38/sites/testsite4/Style

%20Library/Pages/InventoryTreeMap/jquery.corner.js"></script>


<script language="javascript" type="text/javascript" src="http://gblon-i-dw38/sites/testsite4/Style%20Library/Pages/InventoryTreeMap/jit-

yc.js"></script>
<script language="javascript" type="text/javascript" src="http://gblon-i-dw38/sites/testsite4/Style

%20Library/Pages/InventoryTreeMap/CFTController.js"></script>
<script language="javascript" type="text/javascript" src="http://gblon-i-dw38/sites/testsite4/Style

%20Library/Pages/InventoryTreeMap/DataModel.js"></script>
<script language="javascript" type="text/javascript" src="http://gblon-i-dw38/sites/testsite4/Style

%20Library/Pages/InventoryTreeMap/TreeMap.js"></script>

<script language="javascript" type="text/javascript" src="http://gblon-i-dw38/sites/testsite4/Style

%20Library/Pages/InventoryTreeMap/InventoryTreeMap.js"></script>

<!--[if IE]><script type="text/javascript" src="http://gblon-i-dw38/sites/testsite4/Style%20Library/Pages/InventoryTreeMap/excanvas.js"></script><!

[endif]-->

<script language="javascript" type="text/javascript" src="http://gblon-i-dw38/sites/testsite4/Style

%20Library/Common/KendoUI/js/kendo.web.min.js"></script>


<link rel="stylesheet" type="text/css" href="http://gblon-i-dw38/sites/testsite4/Style%20Library/Pages/InventoryTreeMap/base.css" />
<link rel="stylesheet" type="text/css" href="http://gblon-i-dw38/sites/testsite4/Style%20Library/Pages/InventoryTreeMap/Treemap.css" />


<link rel="stylesheet" type="text/css" href="http://gblon-i-dw38/sites/testsite4/Style%20Library/Common/KendoUI/Styles/kendo.default.min.css" />
<link rel="stylesheet" type="text/css" href="http://gblon-i-dw38/sites/testsite4/Style%20Library/Common/KendoUI/Styles/kendo.common.min.css" />


<script id="solutionKendoTemplate" type="text/x-kendo-template">
	 
        # for (var i = 0; i < CFTSolutions.length; i++) { #		
        <li>		
			<div 
				class="solution"
				onclick="javascript:showDetail(this);" 
				solutionid="#= CFTSolutions[i].id #"  
				solutionName="#= CFTSolutions[i].name #"> 			
					<div  id="solutionTitle#= i #" class="solutionNameDiv">#= CFTSolutions[i].name #</div>
					<div  id="solutionDescription#= i #" class="solutionDescriptionDiv result-item more" >#= CFTSolutions

[i].data.SolutionType #</div>		 
			</div>
        </li>
		
		# } #
 
</script>
<script id="attachmentItem" type="text/x-kendo-template">
        <li>
			<a href="#= serverRelativeUrl #" target="_blank">#= name #</a>
        </li>
</script>
<script id="solutionResultItemData" type="text/x-kendo-template">
		<div style="padding-top: 3px; padding-bottom: 3px; color: \#0072bc">#= getNoneNullString(solutionName) #</div>
		<div style="padding-bottom: 3px; padding-right: 18px; font-style: italic" class="result-item more">#= getNoneNullString

(solutionDescription) #</div>
</script>
<script id="solutionDetailContainer" type="text/x-kendo-template">
       	<div id="detailItem#= solutionId #"></div>
</script>
<script id="solutionDetailItem" type="text/x-kendo-template">
        <!--<div style="border: 1px solid lightgrey; padding: 12px" class="item-detail">-->
		<div id="detailTabsContainer#= layout ##= data.ID #" class="item-detail">
			<div style="float: right; margin-top: 8px; margin-right: 12px; z-index:2999;">
				<a href="javascript:void(SP.UI.ModalDialog.showModalDialog({title: 'Edit #= data.Title #', width: 720, url: 

'../Lists/CFTInventory/EditForm.aspx?ID=#= data.ID #&IsDlg=true', dialogReturnValueCallback: function(e) { refreshDetail(e, #= data.ID #) 

}}))">Edit</a>				
				&nbsp;
				<a href="javascript:CloseItemDetail();">X</a>
			</div>
			<div id="detailTabs#= layout ##= data.ID #">
				<ul>
					<li class="k-state-active">
						General Information
					</li>
					<li>
						Technical Information
					</li>
					<li>
						Attachments
					</li>
				</ul>
				<div>
					<table cellpadding="0" cellspacing="0" class="CFTSolutionDetail">
						<tr>
							<td class="row-heading">Name:</td>
							<td class="row-detail"><a href="#= data.URL #" title="#= data.Name1 #">#= data.Name1 

#</a></td>
						</tr>
						<tr>
							<td class="row-heading">Description:</td>
							<td class="row-detail">#= getNoneNullString(data.Description) #</td>
						</tr>
						<tr>
							<td class="row-heading">Product Owner:</td>
							<td class="row-detail">#= getNoneNullString(data.ProductOwner) #</td>
						</tr>
						<tr>
							<td class="row-heading">Business Process Steps:</td>
							<td class="row-detail">#= getNoneNullString(data.BusinessProcessSteps) #</td>
						</tr>
						<tr>
							<td class="row-heading">New Sales and Renewals:</td>
							<td class="row-detail">#= getNoneNullString(data.NewSalesAndRenewals) #</td>
						</tr>
						<tr>
							<td class="row-heading">Programme Development and Placement:</td>
							<td class="row-detail">#= getNoneNullString(data.ProgrammeDevelopmentandPlacement) #</td>
						</tr>
						<tr>
							<td class="row-heading">Billing/A&S:</td>
							<td class="row-detail">#= getNoneNullString(data.BillingOrAAndS) #</td>
						</tr>
						<tr>
							<td class="row-heading">Post Inception Service:</td>
							<td class="row-detail">#= getNoneNullString(data.PostInceptionService) #</td>
						</tr>
						<tr>
							<td class="row-heading">Claims:</td>
							<td class="row-detail">#= getNoneNullString(data.Claims) #</td>
						</tr>
						<tr>
							<td class="row-heading">Solution Type:</td>
							<td class="row-detail">#= getNoneNullString(data.SolutionType) #</td>
						</tr>
						<tr>
							<td class="row-heading">Publications:</td>
							<td class="row-detail">#= getNoneNullString(data.Publications) #</td>
						</tr>
						<tr>
							<td class="row-heading">Transactions and Workflow:</td>
							<td class="row-detail">#= getNoneNullString(data.TransactionsAndWorkflow) #</td>
						</tr>
						<tr>
							<td class="row-heading">Data Intensive:</td>
							<td class="row-detail">#= getNoneNullString(data.DataIntensive) #</td>
						</tr>
						<tr>
							<td class="row-heading">Collaboration:</td>
							<td class="row-detail">#= getNoneNullString(data.Collaboration) #</td>
						</tr>
						<tr>
							<td class="row-heading">Location:</td>
							<td class="row-detail">#= getNoneNullString(data.CILocation) #</td>
						</tr>
						<tr>
							<td class="row-heading">Framework:</td>
							<td class="row-detail">#= getNoneNullString(data.Framework) #</td>
						</tr>
						<tr>
							<td class="row-heading">Integrated/Standalon/Mix:</td>
							<td class="row-detail">#= getNoneNullString(data.IntegratedOrStandalonOrMix) #</td>
						</tr>
						<tr>
							<td class="row-heading">Developed by:</td>
							<td class="row-detail">#= getNoneNullString(data.DevelopedBy) #</td>
						</tr>
						
					</table>
				</div>
				<div>
					<table cellpadding="0" cellspacing="0" style="width: 600px; border: none">
						<tr>
							<td class="row-heading">Global/Re:</td>
							<td class="row-detail">#= getNoneNullString(data.GlobalOrRe) #</td>
						</tr>
						<tr>
							<td class="row-heading">Large:</td>
							<td class="row-detail">#= getNoneNullString(data.Large) #</td>
						</tr>
						<tr>
							<td class="row-heading">Mid-Market:</td>
							<td class="row-detail">#= getNoneNullString(data.MidMarket) #</td>
						</tr>
						<tr>
							<td class="row-heading">Small Commercial:</td>
							<td class="row-detail">#= getNoneNullString(data.SmallCommercial) #</td>
						</tr>
						<tr>
							<td class="row-heading">Affinity:</td>
							<td class="row-detail">#= getNoneNullString(data.Affinity) #</td>
						</tr>
						<tr>
							<td class="row-heading">Captives:</td>
							<td class="row-detail">#= getNoneNullString(data.Captives) #</td>
						</tr>
						<tr>
							<td class="row-heading">Is Portable:</td>
							<td class="row-detail">#= getNoneNullString(data.IsPortable) #</td>
						</tr>
						<tr>
							<td class="row-heading">Portability Comments:</td>
							<td class="row-detail">#= getNoneNullString(data.PortabilityComments) #</td>
						</tr>
						<tr>
							<td class="row-heading">Costs Associated with Setting up:</td>
							<td class="row-detail">#= getNoneNullString(data.Costsassociatedwithsettingup) #</td>
						</tr>
						<tr>
							<td class="row-heading">Costs of Further Deployment:</td>
							<td class="row-detail">#= getNoneNullString(data.Costsoffurtherdeployment) #</td>
						</tr>
						<tr>
							<td class="row-heading">Revenue Generating/Business Model/Price</td>
							<td class="row-detail">#= getNoneNullString(data.RevenueGeneratingOrBusinessModelOrPrice) 

#</td>
						</tr>
						<tr>
							<td class="row-heading">Number of Clients:</td>
							<td class="row-detail">#= getNoneNullString(data.NumberOfClients) #</td>
						</tr>
						<tr>
							<td class="row-heading">Any Readily Available Usage Metrics?</td>
							<td class="row-detail">#= getNoneNullString(data.AnyReadilyAvailableUsageMetrics) #</td>
						</tr>
						<tr>
							<td class="row-heading">Languages Supported:</td>
							<td class="row-detail">#= getNoneNullString(data.LanguagesSupported) #</td>
						</tr>
						<tr>
							<td class="row-heading">BarriersToFurtherAdoption:</td>
							<td class="row-detail">#= getNoneNullString(data.BarriersToFurtherAdoption) #</td>
						</tr>
						<tr>
							<td class="row-heading">Data Source:</td>
							<td class="row-detail">#= getNoneNullString(data.DataSource) #</td>
						</tr>
						<tr>
							<td class="row-heading">Application Status:</td>
							<td class="row-detail">#= getNoneNullString(data.ApplicationStatus) #</td>
						</tr>
						<tr>
							<td class="row-heading">Status Commnents:</td>
							<td class="row-detail">#= getNoneNullString(data.StatusCommnents) #</td>
						</tr>
						<tr>
							<td class="row-heading">Applicable Client Segments:</td>
							<td class="row-detail">#= getNoneNullString(data.CITrainingComment) #</td>
						</tr>
					</table>
				</div>
				<div>
					<ul id="attachmentsList#= layout ##= data.ID #">
						<li>No attachments</li>
					</ul>
				</div> 
			</div>
		</div>
		<!--</div>-->
</script>

<br />
<br />


<table id="CFTInventory">
    <tr>
        <td valign="top" align="left" style="width: 73%;">   
		<div id="solutionDetail"></div>
            <div id="infovis"></div>
        </td>
        <td valign="top" align="left" style="">

            <div id="searchWrapper">


                <div id="searchContainer">
                    <table align="left" valign="top" class="searchPanelRight">
                        <tr>
                            <td>
                                <div class="searchPanel">
                                    <div class="searchPanelTextbox">
                                        <input id="searchBox" type="text">
                                    </div>
                                    <div class="searchPanelButtons">
                                        <input type="button" value="Search" onclick="javascript: loadInventoryData();" />
                                        <input type="button" value="Clear" onclick="javascript: ClearSearch();" />
                                    </div>
                                </div>
                            </td>
                        </tr>
                        <tr>
                            <td>

                                <table class="filters" cellpadding="5">
                                    <tr>
                                        <td>
                                            <input
                                                type="radio"
                                                name="level1Field"
                                                value="SolutionType"
                                                valuesarray="Transactions and Workflow,Data Intensive,Publication,Collaboration"
                                                colours="#8C060C,#623448,#7F7263,#284637,#021E43,#8894A4"
                                                checked="true">Solution Type</input>
                                        </td>
                                        <td>
                                            <select name="filterDropDowns" fieldname="SolutionType" class="filterDropDowns">
                                                <option value="">(select)</option>
                                                <option value="Transactions and Workflow">Transactions and Workflow</option>
                                                <option value="Data Intensive">Data Intensive</option>
                                                <option value="Publication">Publication</option>
                                                <option value="Collaboration">Collaboration</option>
                                            </select>
                                        </td>
                                    </tr>
                                    <tr>
                                        <td>
                                            <input
                                                type="radio"
                                                name="level1Field"
                                                value="BusinessProcessSteps"
                                                valuesarray="Post Inception service,Programme development and Placement,Claims,Billing,Proposing and 

documentation,New Sales and Renewals"
                                                colours="#8C060C,#623448,#7F7263,#284637,#021E43,#8894A4">Process Step</input>
                                        </td>

                                        <td>
                                            <select name="filterDropDowns" fieldname="BusinessProcessSteps" class="filterDropDowns">
                                                <option value="">(select)</option>
                                                <option value="Transactions and Workflow">Post Inception service</option>
                                                <option value="Programme development and Placement">Programme development and Placement</option>
                                                <option value="Claims">Claims</option>
                                                <option value="Billing">Billing</option>
                                                <option value="Proposing and documentation">Proposing and documentation</option>
                                                <option value="New Sales and Renewals">New Sales and Renewals</option>
                                            </select>
                                        </td>
                                    </tr>

                                </table>

                                <br />

                                <div id="solutionListContainer">
                                    <div class="scroll scroll-top">
                                        <span>Scroll up</span>
                                    </div>

                                    <div id="solutionListDiv">
                                        <ul id="solutionList">
                                        </ul>
                                    </div>

                                    <div class="scroll scroll-bottom">
                                        <span>Scroll down</span>
                                    </div>


                                </div>

                            </td>
                        </tr>

                    </table>


                </div>
        </td>


    </tr>
    <tr>

        <td align="center"></td>
        <td>&nbsp;
        </td>
    </tr>
</table>
