/**
 * =====================      Evidence práce       =====================
 * ===================== Ing. Pavel Kříž, (c) 2025 =====================
 * ===================== Upraveno pro PWA aplikaci =====================
 * Verze: 007 - s mapováním pro novou PWA
 */

function doGet(event) {
  var actions = ["testfunction","getlistofcontracts","getlistofactivecontracts","getlistofjobs","getlistofactivejobs","getlistofworkers","getlistofactiveworkers","getlistofadminworkers","getlistofrates","getworkerrate","getrateofworkerbyworkeridandtime","getlistofrecords","getlistoflastrecords","getlistoflastrecordsbyworkerid","addrecord","updaterecord","setpaymentrequest","setpaymentrequestlunch","getlistofpaymentsbyworkerid","getlistoflastpaymentsbyworkerid","getlistofpaymentsbyworkeridanddates","getlistofrecordsbyworkeridanddates","getlistofrecordsbydate","getlistofrecordsbyworkerid","getlistofrecordsbycontractid","getlistofrecordswithratesbyworkeridanddates","getbalancebyworkeridanddates","getlunchpricebydate","getlistoflunchesbydates","getlistoflastlunchesbyworkerid"];

  var output, code = "", error = "", version = "007";
  var action = event.parameter.action || "";
  var id = event.parameter.id || "";
  var data = [];
  action = action.toLowerCase();

  // ============ MAPOVÁNÍ PRO PWA ============
  if (action == "get") {
    const type = event.parameter.type;
    if (type === "contracts") action = "getlistofactivecontracts";
    if (type === "jobs") action = "getlistofactivejobs";  
    if (type === "workers") action = "getlistofactiveworkers";
    if (type === "admins") action = "getlistofadminworkers";
  }
  if (action == "saverecord") action = "addrecord";
  if (action == "savelunch") action = "setpaymentrequestlunch";
  if (action == "saveadvance") action = "setpaymentrequest";
  if (action == "getsummary") action = "getbalancebyworkeridanddates";
  if (action == "getrecords") action = "getlistofrecordsbyworkeridanddates";
  if (action == "getlastrecords") action = "getlistoflastrecordsbyworkerid";
  if (action == "getlastpayments") action = "getlistoflastpaymentsbyworkerid";

  // ============ AKCE ============
  if (action == "getbalancebyworkeridanddates"){ output = getBalanceByWorkerIdAndDates(event.parameter.id, event.parameter.date_fr, event.parameter.date_to); code = output[0]; data = output[1]; }
  if (action == "getlunchpricebydate"){ output = getLunchPriceByDate(event.parameter.date); code = output[0]; data = output[1]; }
  if (action == "getlistoflunchesbydates"){ output = getListOfLunchesByDates(event.parameter.date_fr, event.parameter.date_to); code = output[0]; data = output[1]; }
  if (action == "getlistoflastlunchesbyworkerid"){ output = getListOfLastLunchesByWorkerId(event.parameter.id, event.parameter.count); code = output[0]; data = output[1]; }
  if (action == "getlistofrecordswithratesbyworkeridanddates"){ output = getListOfRecordsWithRatesByWorkerIdAndDates(event.parameter.id, event.parameter.date_fr, event.parameter.date_to); code = output[0]; data = output[1]; }
  if (action == "getlistofrecordsbyworkerid"){ output = getListOfRecordsByWorkerId(event.parameter.id); code = output[0]; data = output[1]; }
  if (action == "getlistofrecordsbycontractid"){ output = getListOfRecordsByContractId(event.parameter.id); code = output[0]; data = output[1]; }
  if (action == "getlistofpaymentsbyworkerid"){ output = getListOfPaymentsByWorkerId(event.parameter.id, event.parameter.date_fr, event.parameter.date_to); code = output[0]; data = output[1]; }
  if (action == "getlistofpaymentsbyworkeridanddates"){ output = getListOfPaymentsByWorkerIdAndDates(event.parameter.id, event.parameter.date_fr, event.parameter.date_to); code = output[0]; data = output[1]; }
  if (action == "getlistofrecordsbyworkeridanddates"){ output = getListOfRecordsByWorkerIdAndDates(event.parameter.id, event.parameter.date_fr, event.parameter.date_to, event.parameter.names || false); code = output[0]; data = output[1]; }
  if (action == "getlistofrecordsbydate"){ output = getListOfRecordsByDate(event.parameter.date); code = output[0]; data = output[1]; }
  if (action == "getrateofworkerbyworkeridandtime"){ data = getRateOfWorkerByWorkerIdAndTime(event.parameter.id.toString(), parseInt(event.parameter.time)); }
  if (action == "getlistoflastpaymentsbyworkerid"){ output = getListOfLastPaymentsByWorkerId(event.parameter.id.toString(), parseInt(event.parameter.count)); code = output[0]; data = output[1]; }
  if (action == "getlistoflastrecordsbyworkerid"){ output = getListOfLastRecordsByWorkerId(event.parameter.id.toString(), parseInt(event.parameter.count)); code = output[0]; data = output[1]; }
  if (action == "testfunction"){ output = testFunction(); code = output[0]; data = output[1]; }
  if (action == "getlistofworkers"){ output = getListOfWorkers(); code = output[0]; data = output[1]; }
  if (action == "getlistofactiveworkers"){ output = getListOfActiveWorkers(); code = output[0]; data = output[1]; }
  if (action == "getlistofadminworkers"){ output = getListOfAdminWorkers(); code = output[0]; data = output[1]; }
  if (action == "getlistofrates"){ output = getListOfRates(); code = output[0]; data = output[1]; }
  if (action == "getworkerrate"){ output = getWorkerRate(id); code = output[0]; data = output[1]; }
  if (action == "getlistofcontracts"){ output = getListOfContracts(); code = output[0]; data = output[1]; }
  if (action == "getlistofactivecontracts"){ output = getListOfActiveContracts(); code = output[0]; data = output[1]; }
  if (action == "getlistofjobs"){ output = getListOfJobs(); code = output[0]; data = output[1]; }
  if (action == "getlistofactivejobs"){ output = getListOfActiveJobs(); code = output[0]; data = output[1]; }
  if (action == "getlistofrecords"){ output = getListOfRecords(); code = output[0]; data = output[1]; }
  if (action == "getlistoflastrecords"){ output = getListOfLastRecords(event.parameter.count); code = output[0]; data = output[1]; }
  if (action == "addrecord"){ var d = []; d[0] = event.parameter.id_contract; d[1] = event.parameter.id_worker; d[2] = getRateOfWorkerByWorkerIdAndTime(event.parameter.id_worker, event.parameter.time_fr); d[3] = event.parameter.id_job; d[4] = event.parameter.time_fr; d[5] = event.parameter.time_to; code = addRecord(d); }
  if (action == "updaterecord"){ var o = [], n = []; o[0] = event.parameter.id_contract; o[1] = n[1] = event.parameter.id_worker; o[2] = n[2] = getRateOfWorkerByWorkerIdAndTime(event.parameter.id_worker, event.parameter.time_fr); o[3] = event.parameter.id_job; o[4] = event.parameter.time_fr; o[5] = event.parameter.time_to; n[0] = event.parameter.id_contract_updated; n[3] = event.parameter.id_job_updated; n[4] = event.parameter.time_fr_updated; n[5] = event.parameter.time_to_updated; code = updateRecord(o, n); }
  if (action == "setpaymentrequest"){ var d = [event.parameter.id_worker, event.parameter.time, event.parameter.name_worker, event.parameter.date, event.parameter.payment, event.parameter.payment_reason]; code = setPaymentRequest(d); }
  if (action == "setpaymentrequestlunch"){ var d = [event.parameter.id_worker, event.parameter.time, event.parameter.name_worker, event.parameter.date]; code = setPaymentRequestLunch(d); }

  if (!action){ code = "100"; error = "Parameter action is missing."; }
  if (actions.indexOf(action) === -1){ code = "101"; error = "Unknown value of action parameter."; }
  if (code == "200"){ error = "Error reading data from sheet."; }
  if (code == "201"){ error = "Sheet doesn't exist."; }
  if (code == "300"){ error = "Error writing data to sheet."; }
  if (code == "301"){ error = "Duplicate record."; }

  return ContentService.createTextOutput(JSON.stringify({code: code, error: error, version: version, action: action, ts: new Date().getTime(), data: data})).setMimeType(ContentService.MimeType.JSON);
}

function getListOfSheetFullNames(){ var s = SpreadsheetApp.getActiveSpreadsheet().getSheets(), n = []; for (var i = 0; i < s.length; i++){ n.push(s[i].getName()); } return n; }
function getSheetFullName(name){ var n = getListOfSheetFullNames(), s = ""; for (var i = 0; i < n.length; i++){ if (n[i] == name){ s = n[i].toLowerCase(); }} return s; }
function getWorkerRate(id){ var w = getListOfWorkers(), r = 0; for (var i = 0; i < w.length; i++){ if (w[i][0] == id){ r = w[i][2]; }} return r; }

function getListOfContracts(){ var s = SpreadsheetApp.getActiveSpreadsheet().getSheetByName("zakázky"), c = "000"; if (s){ try{ [h, ...data] = s.getRange(1, 1, s.getLastRow(), 3).getValues(); } catch { c = "200"; }} else { c = "201"; } return [c, data]; }
function getListOfActiveContracts(){ var s = SpreadsheetApp.getActiveSpreadsheet().getSheetByName("zakázky"), c = "000", d = []; if (s){ try{ [h, ...t] = s.getRange(1, 1, s.getLastRow(), 3).getValues(); } catch { c = "200"; }} else { c = "201"; } if (t.length){ for (var i = 0; i < t.length; i++){ if (t[i][2] == "Y"){ d.push(t[i]); }}} return [c, d]; }
function getListOfJobs(){ var s = SpreadsheetApp.getActiveSpreadsheet().getSheetByName("práce"), c = "000"; if (s){ try{ [h, ...data] = s.getRange(1, 1, s.getLastRow(), 3).getValues(); } catch { c = "200"; }} else { c = "201"; } return [c, data]; }
function getListOfActiveJobs(){ var s = SpreadsheetApp.getActiveSpreadsheet().getSheetByName("práce"), c = "000", d = []; if (s){ try{ [h, ...t] = s.getRange(1, 1, s.getLastRow(), 3).getValues(); } catch { c = "200"; }} else { c = "201"; } if (t.length){ for (var i = 0; i < t.length; i++){ if (t[i][2] == "Y"){ d.push(t[i]); }}} return [c, d]; }
function getListOfWorkers(){ var s = SpreadsheetApp.getActiveSpreadsheet().getSheetByName("pracovníci"), c = "000"; if (s){ try{ [h, ...data] = s.getRange(1, 1, s.getLastRow(), 4).getValues(); } catch { c = "200"; }} else { c = "201"; } return [c, data]; }
function testFunction(){ return getListOfWorkers(); }
function getListOfActiveWorkers(){ var s = SpreadsheetApp.getActiveSpreadsheet().getSheetByName("pracovníci"), c = "000", d = []; if (s){ try{ [h, ...t] = s.getRange(1, 1, s.getLastRow(), 4).getValues(); } catch { c = "200"; }} else { c = "201"; } if (t.length){ for (var i = 0; i < t.length; i++){ if (t[i][2] == "Y"){ d.push(t[i]); }}} return [c, d]; }
function getListOfAdminWorkers(){ var s = SpreadsheetApp.getActiveSpreadsheet().getSheetByName("pracovníci"), c = "000", d = []; if (s){ try{ [h, ...t] = s.getRange(1, 1, s.getLastRow(), 4).getValues(); } catch { c = "200"; }} else { c = "201"; } if (t.length){ for (var i = 0; i < t.length; i++){ if (t[i][2] == "Y" && t[i][3] == "Y"){ d.push(t[i]); }}} return [c, d]; }
function getListOfRates(){ var s = SpreadsheetApp.getActiveSpreadsheet().getSheetByName("hodinové sazby"), c = "000"; if (s){ try{ [h, ...data] = s.getRange(1, 1, s.getLastRow(), 5).getValues(); } catch { c = "200"; }} else { c = "201"; } return [c, data]; }
function getListOfRecords(){ var s = SpreadsheetApp.getActiveSpreadsheet().getSheetByName("záznamy"), c = "000"; if (s){ try{ [h, ...data] = s.getRange(1, 1, s.getLastRow(), 6).getValues(); } catch { c = "200"; }} else { c = "201"; } return [c, data]; }
function getListOfRecordsByWorkerId(id){ var o = getListOfRecords(), c = o[0], t = o[1], d = []; if (c == "000"){ for (var i = 0; i < t.length; i++){ if(id == t[i][1]){ d.push(t[i]); }}} return [c, d]; }
function getListOfRecordsByContractId(id){ var o = getListOfRecords(), c = o[0], t = o[1], d = []; if (c == "000"){ for (var i = 0; i < t.length; i++){ if(id == t[i][0]){ d.push(t[i]); }}} return [c, d]; }
function getListOfLastRecords(count){ var s = SpreadsheetApp.getActiveSpreadsheet().getSheetByName("záznamy"), c = "000"; if (s){ try{ var l = s.getLastRow(), f = count >= l ? 1 : l - count; [h, ...data] = s.getRange(f, 1, l, 6).getValues(); } catch { c = "200"; }} else { c = "201"; } return [c, data]; }

function getListOfLastRecordsByWorkerId(id, count){ 
  var o = getListOfRecords(), c = o[0], t = o[1], dIn = [], d = []; 
  if (c == "000"){ 
    for (var i = 0; i < t.length; i++){ if (id == t[i][1]){ dIn.push(t[i]); }} 
    if (dIn.length > count){ for (var i = dIn.length - count; i < dIn.length; i++){ d.push(dIn[i]); }} 
    else { for (var i = 0; i < dIn.length; i++){ d.push(dIn[i]); }}
  }
  var o2 = getContractsIdAndName(), c2 = o2[0], ids2 = o2[1];
  if (c2 == "000"){ for (var i = 0; i < d.length; i++){ for (var j = 0; j < ids2.length; j++){ if (d[i][0] == ids2[j][0]){ d[i][0] = ids2[j][1]; }}}}
  var o3 = getJobsIdAndName(), c3 = o3[0], ids3 = o3[1];
  if (c3 == "000"){ for (var i = 0; i < d.length; i++){ for (var j = 0; j < ids3.length; j++){ if (d[i][3] == ids3[j][0]){ d[i][3] = ids3[j][1]; }}}}
  return [c, d]; 
}

function getListOfPayments(){ var s = SpreadsheetApp.getActiveSpreadsheet().getSheetByName("zálohy"), c = "000"; if (s){ try{ [h, ...data] = s.getRange(1, 1, s.getLastRow(), 6).getValues(); } catch { c = "200"; }} else { c = "201"; } return [c, data]; }

function getLunchPriceByDate(date){ 
  var s = SpreadsheetApp.getActiveSpreadsheet().getSheetByName("ceny obědů"), c = "000", p = null; 
  if (s){ try{ [h, ...data] = s.getRange(1, 1, s.getLastRow(), 3).getValues(); } catch{ c = "200"; }} else { c = "201"; }
  if (data.length){ 
    for (var i = 0; i < data.length; i++){ 
      var tF = getTimeFromDate(data[i][1]), tT = getTimeFromDate(data[i][2]), t = getTimeFromDate(date);
      if (t >= tF && t <= tT){ p = 1*data[i][0]; }
    }
  }
  return [c, p]; 
}

function getListOfLunchesByDates(dateFr, dateTo){ 
  var o = getListOfPayments(), c = o[0], t = o[1], d = [];
  if (c === "000"){ 
    for (var i = 0; i < t.length; i++){ 
      var time = getTimeFromDate(t[i][3]), tF = getTimeFromDate(dateFr), tT = getTimeFromDate(dateTo) + 86400000 - 1000;
      if (time >= tF && time <= tT && t[i][5] == "oběd"){ d.push(t[i]); }
    }
  }
  return [c, d]; 
}

function getListOfLastLunchesByWorkerId(id, count){ 
  var o = getListOfPayments(), c = o[0], t = o[1], d = [];
  if (c === "000"){ for (var i = 0; i < t.length; i++){ if (t[i][0] == id && t[i][5] == "oběd"){ d.push(t[i]); }}}
  return [c, d.slice(-count)]; 
}

function getListOfPaymentsByWorkerId(id){ var o = getListOfPayments(), c = o[0], t = o[1], d = []; if (c == "000"){ for (var i = 0; i < t.length; i++){ if (id == t[i][0]){ d.push(t[i]); }}} return [c, d]; }

function getListOfLastPaymentsByWorkerId(id, count){ 
  var o = getListOfPaymentsByWorkerId(id), c = o[0], t = o[1], d = [];
  if (c == "000"){ 
    if (t.length > count){ for (var i = t.length - count; i < t.length; i++){ d.push(t[i]); }} 
    else { for (var i = 0; i < t.length; i++){ d.push(t[i]); }}
  }
  return [c, d]; 
}

function addRecord(dataToWrite) {
  var s = SpreadsheetApp.getActiveSpreadsheet().getSheetByName(getSheetFullName("záznamy")), c = "000", wId = dataToWrite[1];
  if (s) {
    try {
      var o = getListOfRecordsByWorkerId(wId), ex = o[1], cG = o[0];
      if(cG != "000"){ return cG; }
      var isDup = false;
      for (var i = 0; i < ex.length; i++) { if (arraysEqual(ex[i], dataToWrite)) { isDup = true; break; }}
      if (!isDup) {
        var wName = getWorkerNameById(wId), sT = msToDateTime(dataToWrite[4]), eT = msToDateTime(dataToWrite[5]);
        var tH = Number(((dataToWrite[5] - dataToWrite[4])/3600000).toFixed(3)), note = "vyplněno automaticky";
        var all = [...dataToWrite, wName, tH, sT, eT, note];
        s.getRange(s.getLastRow() + 1, 1, 1, 11).setValues([all]);
        c = "000";
      } else { c = "301"; }
    } catch (e) { c = "300"; }
  } else { c = "201"; }
  return c;
}

function arraysEqual(a, b) { if (a.length !== b.length) return false; for (var i = 0; i < a.length; i++) { if (a[i] !== b[i]) return false; } return true; }

function updateRecord(oldR, newR){
  var o = getListOfRecords(), cR = o[0], d = o[1], rIdx = null;
  for (var i = 0; i < d.length; i++){ if (d[i][0] == oldR[0] && d[i][1] == oldR[1] && d[i][3] == oldR[3] && d[i][4] == oldR[4] && d[i][5] == oldR[5]){ rIdx = i+2; }}
  var s = SpreadsheetApp.getActiveSpreadsheet().getSheetByName(getSheetFullName("záznamy")), c = "000";
  if (s && cR == "000"){ try{ s.getRange(rIdx, 1, 1, 6).setValues([newR]); c = "000"; } catch(e) { c = "300"; }} else { c = "201"; }
  return c;  
}

function setPaymentRequest(dataToWrite){ 
  var s = SpreadsheetApp.getActiveSpreadsheet().getSheetByName("zálohy"), c = "000";
  if (s){ try{ s.getRange(s.getLastRow() + 1, 1, 1, 6).setValues([dataToWrite]); c = "000"; } catch(e) { c = "300"; }} else { c = "201"; }
  return c;  
}

function setPaymentRequestLunch(dataToWrite){ 
  var s = SpreadsheetApp.getActiveSpreadsheet().getSheetByName("zálohy"), c = "000";
  if (s){ 
    try{ 
      var date = dataToWrite[3], o = getLunchPriceByDate(date), cL = o[0], price = o[1];
      if (cL == "000" && price){ dataToWrite.push(price); dataToWrite.push("oběd"); }
      s.getRange(s.getLastRow() + 1, 1, 1, 6).setValues([dataToWrite]);
      c = "000";
    } catch(e) { c = "300"; }
  } else { c = "201"; }
  return c;  
}

function getTimesFromDates(d1, d2){ var a1 = d1.split(". "), dt1 = new Date(a1[2] + "-" + a1[1] + "-" + a1[0]), t1 = dt1.getTime(); var a2 = d2.split(". "), dt2 = new Date(a2[2] + "-" + a2[1] + "-" + a2[0]), t2 = dt2.getTime(); var tz = (new Date()).getTimezoneOffset() * 60000; return [t1 + tz, t2 + tz + 86400000 - 1000]; }

function getRateOfWorkerByWorkerIdAndTime(id, time){ 
  var o = getListOfRates(), c = o[0], d = o[1], rate; 
  if (c == "000"){ 
    for (var i = 0; i < d.length; i++){ 
      if (d[i][0].toString() == id && time >= getTimeFromDate(d[i][3]) && time <= getTimeFromDate(d[i][4]) + 86400000 - 1000){ rate = d[i][2]; }
    }
    return rate;
  }
  return "???";
}

function getListOfPaymentsByWorkerIdAndDates(id, dateFr, dateTo){ 
  var o = getListOfPaymentsByWorkerId(id), c = o[0], t = o[1], d = [];
  var tF = getTimeFromDate(dateFr), tT = getTimeFromDate(dateTo) + 86400000 - 1000;
  if (c == "000"){ for (var i = 0; i < t.length; i++){ var time = t[i][1]; if(time >= tF && time <= tT){ d.push(t[i]); }}}
  return [c, d]; 
}

function getListOfRecordsByWorkerIdAndDates(id, dateFr, dateTo, names){ 
  var o = getListOfRecordsByWorkerId(id), c = o[0], t = o[1], d = [];
  var tF = getTimeFromDate(dateFr), tT = getTimeFromDate(dateTo) + 86400000 - 1000;
  if (c == "000"){ for (var i = 0; i < t.length; i++){ var time = t[i][4]; if(time >= tF && time <= tT){ d.push(t[i]); }}}
  if (c == "000" && names){
    var o2 = getContractsIdAndName(), c2 = o2[0], ids2 = o2[1];
    if (c2 == "000"){ for (var i = 0; i < d.length; i++){ for (var j = 0; j < ids2.length; j++){ if (d[i][0] == ids2[j][0]){ d[i][0] = ids2[j][1]; }}}} else { c = c2; }
    var o3 = getJobsIdAndName(), c3 = o3[0], ids3 = o3[1];
    if (c3 == "000"){ for (var i = 0; i < d.length; i++){ for (var j = 0; j < ids3.length; j++){ if (d[i][3] == ids3[j][0]){ d[i][3] = ids3[j][1]; }}}} else { c = c3; }
  }
  return [c, d]; 
}

function getListOfRecordsByDate(date){ 
  var o = getListOfRecords(), c = o[0], t = o[1], d = [];
  if (c == "000"){ for (var i = 0; i < t.length; i++){ var _t = 1*t[i][4], _d = getDateFromTime(_t); if(_d == date){ d.push(t[i]); }}}
  return [c, d]; 
}

function getListOfRecordsWithRatesByWorkerIdAndDates(id, dateFr, dateTo){ 
  var o = getListOfRecordsByWorkerIdAndDates(id, dateFr, dateTo), c = o[0], t = o[1], d = [];
  if (c == "000" && t.length){ for (var i = 0; i < t.length; i++){ var time = t[i][4], rate = getRateOfWorkerByWorkerIdAndTime(id, time); d.push([t[i][4], t[i][5], rate]); }}
  return [c, d]; 
}

function getBalanceByWorkerIdAndDates(id, dateFr, dateTo){ 
  var o1 = getListOfRecordsWithRatesByWorkerIdAndDates(id, dateFr, dateTo), c1 = o1[0], t1 = o1[1];
  var o2 = getListOfPaymentsByWorkerIdAndDates(id, dateFr, dateTo), c2 = o2[0], t2 = o2[1];
  var sE = 0, sP = 0, sH = 0, h = 0, c = "000", d = [];
  if (c1 == "000" && t1.length){ for (var i = 0; i < t1.length; i++){ h = ((t1[i][1] - t1[i][0]) / 3600000).toFixed(2); sE += 1*h * 1*t1[i][2]; sH += 1*h; }}
  if (c2 == "000" && t2.length){ for (var i = 0; i < t2.length; i++){ sP += 1*t2[i][4]; }}
  if (c1 == "000" && c2 == "000"){ d.push(sH, sE, sP); }
  if (c1 != "000"){ c = c1; }
  if (c2 != "000"){ c = c2; }
  return [c, d]; 
}

function msToDateTime(ms){ return new Date(1*ms).toLocaleString("cs-CZ", {day: "2-digit", month: "2-digit", year: "numeric", hour: "2-digit", minute: "2-digit"}); }
function getTimeFromDate(date){ var a = date.split(". "), d = new Date(a[2] + "-" + a[1] + "-" + a[0]), tz = (new Date()).getTimezoneOffset() * 60000; return d.getTime() + tz; }
function getDateFromTime(time){ var tz = (new Date()).getTimezoneOffset() * 60000; return new Date(time + tz).toLocaleString("cs-CZ", {day: "2-digit", month: "2-digit", year: "numeric"}); }

function getContractsIdAndName(){ var s = SpreadsheetApp.getActiveSpreadsheet().getSheetByName("zakázky"), c = "000"; if (s){ try{ [h, ...data] = s.getRange(1, 1, s.getLastRow(), 2).getValues(); } catch { c = "200"; }} else { c = "201"; } return [c, data]; }
function getJobsIdAndName(){ var s = SpreadsheetApp.getActiveSpreadsheet().getSheetByName("práce"), c = "000"; if (s){ try{ [h, ...data] = s.getRange(1, 1, s.getLastRow(), 2).getValues(); } catch { c = "200"; }} else { c = "201"; } return [c, data]; }

function getWorkerNameById(id){
  var s = SpreadsheetApp.getActiveSpreadsheet().getSheetByName("pracovníci"), c = "000", name = "";
  if (s){ try{ [h, ...data] = s.getRange(1, 1, s.getLastRow(), 2).getValues(); for (var i = 0; i < data.length; i++){ if (data[i][0] == id){ name = data[i][1]; }}} catch { c = "200"; }} else { c = "201"; }
  return name;
}

function onOpen(event){ addMenu(); }
function addMenu(){ SpreadsheetApp.getUi().createMenu("Extra").addItem("[ 1 ] Zakázky", "showDialogContracts").addToUi(); }
function showDialogContracts(){ SpreadsheetApp.getUi().showModelessDialog(HtmlService.createHtmlOutputFromFile('dialogContracts'), 'Zakázky'); }
