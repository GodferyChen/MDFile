---
title: �����ܽ� - Android ƪ
grammar_cjkRuby: true
---


1.��ν�һ��Activity���óɴ��ڵ���ʽ��
* ֻ�����嵥�ļ����޸�Activity��theme  android:theme="@android:style/Theme.Dialog"
* �޸�Activity��styles��windowBackground���Զ���һ��drawable

2.�������л���ʱ��Activity���������ڱ仯�����
* ������Activity��android:configChangesʱ�����������µ��ø����������ڣ��к���ʱ��ִ��һ�Σ�������ʱ��ִ������
* ����Activity��android:configChanges="orientation"ʱ���������ǻ����µ��ø����������ڣ��кᡢ����ʱֻ��ִ��һ��
* ����Activity��android:configChanges="orientation|keyboardHidden"ʱ�������������µ��ø����������ڣ�ֻ��ִ��onConfigurationChanged����

3.Activity������ģʽ�м��֣��ֱ���ʲô����ʲô����
* ==Standard== ��׼ģʽ������Ĭ�ϵ�����ģʽ��ÿ�ζ��½�һ��ʵ������
* ==SingleTop== ���������ջ����������ͬ��ʵ�������ã������½���ѹ��ջ��
* ==SingleTask== ���������ջ�з�������ͬ��ʵ�������������������ֹ���Ƴ������ø�ʵ���������½�ʵ������ջ
* ==SingleInstance== ����ͬӦ�ã������̵߳ȹ���һ��ʵ�������۴Ӻ�Ӧ�õ��ø�ʵ��������

4.ImageView��ScaleType�м��֣����ǵ��ص��������ʲô��
* ==matrix==(Ĭ��) ���ı�ԭͼ�Ĵ�С����ImageView�����Ͻǿ�ʼ����ԭͼ��ԭͼ����ImageView�Ĳ������ü�����
* ==center== ����ԭͼ�Ĵ�С����ʾ��ImageView�����ġ���ԭͼ��size����ImageView��size���������ֲü�����
* ==centerCrop== ������ImageViewΪĿ�ģ���ԭͼ�����Ķ�׼ImageVIew�����ģ��ȱ����Ŵ�ԭͼ��ֱ������ImageViewΪֹ��ָ����ImageView�Ŀ�߶�Ҫ��������ԭͼ����ImageView�Ĳ������ü�����
* ==centerInside== ��ԭͼ��ȫ��ʾΪĿ�ģ���ͼƬ����������������ʾ��ͨ����������Сԭͼ��size���ߣ����ڻ�С��ImageView�Ŀ��ߣ������ԭͼ��size�����С��ImageView��size����ԭͼ��size�����κδ���������ʾ��ImageView��
* ==fitCenter== ��ԭͼ�������������С��ImageView�ĸ߶ȣ�������ʾ
* ==fitEnd== ��ԭͼ������������С����ImageView�ĸ߶ȣ���ʾ��ImageView���Ҳ���λ��
* ==fitStart== ��ԭͼ������������С����ImageView�ĸ߶ȣ���ʾ��ImageVIew���󲿷�λ��
* ==fitXY== ��ԭͼ����ָ���Ĵ�С��ImageView����ʾ��������ʾͼƬ��������ԭ����������ImageView

5.View�Ļ�������
* View�Ļ�������==ViewRoot==������ġ�ÿ��Ӧ�ó��򴰿ڵ�DecorView����һ����֮������ViewRoot�������ֹ����Ĺ�ϵ����WindowManage��ά���ġ�
* ==���Ƶ����== ViewRootImpl��performTraversals()����
* �����׶�
  *  measure���ж��Ƿ���Ҫ���¼���view�Ĵ�С����Ҫ�Ļ�����
  *  layout���ж��Ƿ���Ҫ���¼���view��λ�ã���Ҫ�Ļ�����
  *  draw���ж��Ƿ���Ҫ���»���view����Ҫ�Ļ����»���

6.�����¼��Ĵ��ݻ���
*  Android�¼��ַ����ȴ��ݵ�ViewGroup������ViewGroup���ݵ�View�ġ�
*  ��ViewGroup�п���ͨ��onInterceptTouchEvent�������¼����ݽ������أ�onInterceptTouchEvent��������true���������¼���������View���ݣ�����false�������¼��������أ�Ĭ�Ϸ���false��
*  ��View����������ݵ��¼����ѵ���ViewGroup�н��޷����յ��κ��¼���

7.������APP�����ܣ����ԴӲ��֡����롢�ڴ桢����ȷ�������һ��
 * ����
   * ���ٻ��Ʋ��ɼ���UI����
   * �Ƽ�ʹ��==RelativeLayout==����
   * ����==����==�����٣���ƽ����
   * �����򻯲���
 * ����
   * ʹ��==�Ż�==�������ݼ��ϣ�SparseArray��SparseBooleanArray��LongSparseArray��
   * ��������ʹ��==����ע��==���
   * ʹ��==ProGuard==�򻯴���
   * ����ʹ��==����==���
   * ��ʹ��==ö��==����ռ�ڴ��Ǿ�̬������������
   * ���Ƶ�ʹ��Service���Ƽ�ʹ��IntentService��
* �ڴ�
  *  �����治�ɼ�ʱ�ͷ��ڴ�
  *  �ڴ����ʱ�ͷ��ڴ���Դ
  *  ������Bitmap���˷��ڴ�
  *  ֪���ڴ�Ŀ�֧�����Java�����ռ500�ֽڣ�����ʵ��ռ12-16�ֽڣ�
* ����
  *   �����������ݻ�ȡ��Ƶ��
  *    �޷��==GZIP==����������������������죩
  *   ʹ��==SPDY==������ͬһ��socket������ͬһ��������������������
  *   ���SPDY�����ã���ͨ��==���ӳ�==������������ʱ
  *   ==����==��Ӧ�����������ظ�����������
  
7.����Ļ������Դ���Щ�������֣�
* ʹ��wrap_content��math_parent��weight
* ʹ����Բ��֣����þ��Բ���
* ʹ���޶���
  * ʹ�óߴ��޶���
  * ʹ����С����޶���
  * ʹ�ò��ֱ���
  * ʹ����Ļ�����޶���
* ʹ���Զ�����λͼ

8.˵һ˵����ͼƬ���ؿ��ʵ��ԭ��
* Glide �յ����ؼ���ʾ��Դ�����񣬴���Request������RequestManage����Request����Engineȥ����Դ��ȡ��Դ��ͨ��Fetcher������ȡ����Transformation����󽻸�Target

9.˵һ˵�������������ͨ������ʲô��װ��
 *   �޷��==GZIP==����������������������죩
 *   ʹ��==SPDY==������ͬһ��socket������ͬһ��������������������
 *   ���SPDY�����ã���ͨ��==���ӳ�==������������ʱ
 *   ==����==��Ӧ�����������ظ�����������

10.Fragment��Activity������
* Activity��ϵͳ���Ĵ����֮һ����ActivityManage��������������ϵͳ����
* Fragment����3.0��������������FragmentManage����������Activity���ɿ��ƣ��������ɾ����������
* FragmentManage��ActivityManage���л�����ƣ�getFragmentByTag����ById�鿴�㷨�Ƿ��д��ڵ�
* FragmentҲ���Լ����������ڣ����ܵ�Activity����������Ӱ��