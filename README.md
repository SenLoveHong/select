# select
about_wolde
import android.content.Context;
import android.database.sqlite.SQLiteDatabase;
import android.database.sqlite.SQLiteDatabase.CursorFactory;
import android.database.sqlite.SQLiteOpenHelper;
import android.util.Log;

public class OpenHelper extends SQLiteOpenHelper {

	public OpenHelper(Context context) {
		super(context, ConstantManager.DB.DB_NAME, null,
				ConstantManager.DB.DB_VERSION);
		// TODO Auto-generated constructor stub
	}

	@Override
	public void onCreate(SQLiteDatabase arg0) {
		// TODO Auto-generated method stub
		String sql = " CREATE TABLE  " + ConstantManager.DB.CHANNEL_TABLE_NAME
				+ "( " + ConstantManager.DB.CHANNEL_PK_ID
				+ "  INTEGER PRIMARY KEY AUTOINCREMENT ,"
				+ ConstantManager.DB.CHANNEL_ID + "  INT ,"
				+ ConstantManager.DB.CHANNEL_NAME + "  TEXT ,"
				+ ConstantManager.DB.CHANNEL_ORDERID + "  INT ,"
				+ ConstantManager.DB.CHANNEL_ISSELECTED + "  INT ,"
				+ ConstantManager.DB.CHANNEL_URL + "  TEXT )";
		Log.e("频道", sql);
		arg0.execSQL(sql);

		String sqll = "CREATE TABLE " + ConstantManager.DB.USER_TABLE_NAME
				+ "(" + ConstantManager.DB.USER_ID
				+ "  INTEGER  PRIMARY KEY AUTOINCREMENT ,"
				+ ConstantManager.DB.USER_NAME + " TEXT , "
				+ ConstantManager.DB.USER_PWD + " TEXT , "
				+ ConstantManager.DB.USER_EMAIL + " TEXT  )";
		Log.e("用户表", sqll);
		arg0.execSQL(sqll);

		String sqlll = "CREATE TABLE " + ConstantManager.DB.LOGIN_TABLE_NAME
				+ "(" + ConstantManager.DB.LOGIN_ID
				+ "  INTEGER  PRIMARY KEY AUTOINCREMENT ,"
				+ ConstantManager.DB.LOGIN_USER_ID + " TEXT , "
				+ ConstantManager.DB.LOGIN_TIME + " TEXT , "
				+ ConstantManager.DB.LOGIN_DEVICE_ID + " INT  , "
				+ ConstantManager.DB.LOGIN_LOCATION + " TEXT )";
		Log.e("用户表", sqlll);
		arg0.execSQL(sqlll);

		String sqllll = "CREATE TABLE "
				+ ConstantManager.DB.FAVORITE_TABLE_NAME + "("
				+ ConstantManager.DB.FAVORITE_ID
				+ "  INTEGER  PRIMARY KEY AUTOINCREMENT ,"
				+ ConstantManager.DB.FAVORITE_USER_ID + " INT , "
				+ ConstantManager.DB.FAVORITE_NEWS_ID + " TEXT , "
				+ ConstantManager.DB.FAVORITE_NEWS_TITLE + " TEXT  , "
				+ ConstantManager.DB.FAVORITE_NEWS_INTRO + " TEXT  , "
				+ ConstantManager.DB.FAVORITE_NEWS_PIC + " TEXT  , "
				+ ConstantManager.DB.FAVORITE_NEWS_LINK + " TEXT  , "
				+ ConstantManager.DB.LOGIN_LOCATION + " TEXT )";
		Log.e("用户表", sqllll);
		arg0.execSQL(sqllll);
	}

	@Override
	public void onUpgrade(SQLiteDatabase arg0, int arg1, int arg2) {
		// TODO Auto-generated method stub
		String sql = "DROP TABLE " + ConstantManager.DB.CHANNEL_TABLE_NAME;
		arg0.execSQL(sql);
		onCreate(arg0);
	}
}
