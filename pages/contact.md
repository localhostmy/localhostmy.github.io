---
title: Contact Us
subtitle: Contact Us
lead: Feel Free to Contact Us
layout: map
permalink: /contacts/
published: true
order: 8
---

<div class ="card-deck mb-3">
  <div class="card mb-3" >
    <center class="card-header">KLANG VALLEY</center>
    <div class="card-body">
      <center class="card-title"><h4>Localhost Sdn Bhd</h4></center>
      <p class="card-text">
      No 29-2, Tingkat 2, Jalan Tukul N15/N,
      Seksyen 15, 40200 Shah Alam,
      Selangor, Malaysia.</p>
    </div>
    <ul class="list-group list-group-flush">
      <li class="list-group-item">
        <span><i class="fa fa-phone"></i> / <i class="fa fa-fax"></i> +603 5523 4445</span> |
        <span><i class="fa fa-envelope"></i> hello@localhost.my</span>
      </li>
    </ul>
  </div>
  <div class="card mb-3" >
    <center class="card-header">KELANTAN</center>
    <div class="card-body">
      <center class="card-title"><h4>Localhost Sdn Bhd</h4></center>
      <p class="card-text">
      2215-B Jalan Long Yunus,
      Off Taman Maju,
      15150 Kota Bharu,
      Kelantan, Malaysia.</p>
    </div>
  </div>
  <div class="card mb-3" >
    <center class="card-header">HOSTFILE</center>
    <div class="card-body">
      <center class="card-title"><h4>Windows</h4>
      <p class="card-text">Windows/System32/drivers/etc/hosts</p></center>

     <center class="card-title"><h4>Unix/Linux</h4>
      <p class="card-text">/etc/hosts</p></center>
    </div>
  </div>
</div>

<div class ="card mb-3">
  <div class="card-body">
    <form>
      <div class="row">
        <div class="col-md-6">
            <div class="form-group">
              <label for="name">Name</label>
              <div class="input-group">
                <span class="input-group-addon"><i class="fa fa-address-card-o"></i>
                </span>
                <input type="text" class="form-control" id="name" placeholder="Enter name" required="required" />
              </div>
            </div>
            <div class="form-group">
              <label for="email">Email Address</label>
              <div class="input-group">
                <span class="input-group-addon"><i class="fa fa-envelope-o"></i>
                </span>
                <input type="email" class="form-control" id="email" placeholder="Enter email" required="required" />
              </div>
            </div>
            <div class="form-group">
              <label for="subject">Subject</label>
              <div class="input-group">
                <span class="input-group-addon"><i class="fa fa-check"></i>
                </span>
                <select id="subject" name="subject" class="form-control" required="required">
                <option value="na" selected="">Choose One:</option>
                <option value="service">General Customer Service</option>
                <option value="suggestions">Suggestions</option>
                <option value="product">Product Support</option>
              </select>
              </div>
            </div>
        </div>
        <div class="col-md-6">
          <div class="form-group">
            <label for="name">Message</label>
            <textarea name="message" id="message" class="form-control" rows="9" cols="25" required="required" placeholder="Message"></textarea>
          </div>
        </div>
        <div class="col-md-12">
            <button type="submit" class="btn btn-primary pull-right btn-sm" id="btnContactUs"> Send Message</button>
        </div>
      </div>
    </form>
  </div>
</div>
