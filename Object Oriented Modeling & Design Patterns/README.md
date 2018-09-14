## Architectural Design Patterns

# MVC ���� (Model + View + Controller)
 1) Model : ���α׷����� ���Ǵ� �����Ϳ� �����͸� �����ϴ� ������ ó��
 2) View : ����ڿ��� �����Ǵ� UI(User Interface), �������� �κ�
 3) Controller : ������� �Է°� ������ �ް� �Է¿� �°� Model�� �ݿ�, ���ۿ� �°� Model�� �����Ͽ� ������ �°� ó��
 -> ���� : ������, Ȯ�强�� ����.
	   View�� Model ���� ������ ���ϰ� Controller�� �߰� ���� ������ �Ͽ� ���������� ���� ������ ������ ���� �����ϴ�.
    ���� : View�� Model�� ���� �������̴�. �������� ���ٴ� ���� Model�� View�� �Ϻ��� �и��� ��ƴٴ� ���̴�. �̴� ������ ��ȣ���� �� ������ ������ �ʷ��� �� �ִ�.

# MVP ���� (Model + View + Presenter)
 1) Model : ���α׷����� ���Ǵ� �����Ϳ� �����͸� �����ϴ� ������ ó��
 2) View : ����ڿ��� �����Ǵ� UI(User Interface), �������� �κ�
 3) Presenter : View���� ��û�� ������ Model���� �����ؼ� ����
 -> ���� : View�� Model�� �������� �����Ͽ� �Ϻ��ϰ� �и��Ѵ�. ���ÿ� MVC ������ ���� ���� ���� �ִ�.
    ���� : View�� Presenter�� 1:1�� ���� �������� ���´�. MVC ���ϰ� ����ϰ� Model�� Presenter�� �Ϻ��� �и��� ��ƴٴ� ���̴�.

# MVVM ����
 1) Model : ���α׷����� ���Ǵ� ������
 2) View : ����ڿ��� �����Ǵ� UI(User Interface), �������� �κ�
 3) ViewModel : View�� ǥ���ϱ� ���� Model, Command�� ���� ������ �����ϰ� �����͸� ó���Ͽ� Model�� ����
 ���� ����(Behavioral Patterns)�� ���ϴ� Command ���ϰ� ���ü� ����(Concurrency Patterns)�� ���ϴ� Binding Properties ������ �̿��Ͽ�
 View�� ���� �Է��� ������ Command�� ���� ViewModel�� ����� �������� Data Binding���� ���� ViewModel�� ��(��Ȯ���� Model���� �޾ƿ� ������)�� ��ȭ�ϸ� View�� ������ ���ÿ� �ٲ�� �ȴ�.
 -> ���� : ���� MVP ������ ���� �ִ� View�� Presenter�� 1:1 �������� Command ���ϰ� Binding Properties ������ ���� View�� ViewModel�� �����Ͽ� �� �κ��� �������� ������.
    ���� : View�� Presenter�� 1:1�� ���� �������� ���´�. MVC ���ϰ� ����ϰ� Model�� Presenter�� �Ϻ��� �и��� ��ƴٴ� ���̴�.
