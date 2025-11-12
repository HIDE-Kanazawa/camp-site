---
layout: default
title: "お問い合わせ"
permalink: /contact/
---

# お問い合わせ

ご質問、ご意見、ご感想などお気軽にお寄せください。

<form action="https://formspree.io/f/YOUR_FORM_ID" method="POST" class="contact-form">
  <!--
    ★フォームSaaS設定方法★
    1. Formspree (https://formspree.io/) などのサービスに登録
    2. フォームIDを取得
    3. 上記action属性のYOUR_FORM_IDを実際のIDに置き換え

    または他のフォームサービス（Netlify Forms、Google Formsなど）を使用
  -->

  <div class="form-group">
    <label for="name">お名前 <span class="required">*</span></label>
    <input type="text" id="name" name="name" required>
  </div>

  <div class="form-group">
    <label for="email">メールアドレス <span class="required">*</span></label>
    <input type="email" id="email" name="email" required>
  </div>

  <div class="form-group">
    <label for="message">メッセージ <span class="required">*</span></label>
    <textarea id="message" name="message" rows="6" required></textarea>
  </div>

  <button type="submit" class="btn-submit">送信する</button>
</form>
