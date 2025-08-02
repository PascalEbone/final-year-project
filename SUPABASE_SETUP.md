# Supabase Setup Instructions

## Step 1: Create Supabase Tables

1. Go to your [Supabase Dashboard](https://app.supabase.com/)
2. Select your project
3. Go to the **SQL Editor** tab
4. Copy and paste the contents of `supabase_setup.sql` into the editor
5. Click **Run** to execute the SQL

This will create:
- `categories` table for storing income/expense categories
- `transactions` table for storing financial transactions
- `budgets` table for storing budget information
- Row Level Security (RLS) policies for data protection
- Indexes for better performance

## Step 2: Verify Tables Created

1. Go to the **Table Editor** in your Supabase dashboard
2. You should see three new tables: `categories`, `transactions`, and `budgets`
3. Each table should have the correct columns and constraints

## Step 3: Test the App

1. Run your Flutter app: `flutter run`
2. Try adding a transaction - it should now save to Supabase
3. Try adding categories - they should persist
4. Try creating budgets - they should work with cloud sync

## Current Status

✅ **Dropdown Error Fixed**: The budget screen dropdown now works correctly  
✅ **Local Fallback**: App works even without database (stores data locally)  
✅ **Transaction Saving**: Transactions are saved locally when database unavailable  
✅ **Category Loading**: Categories load from defaults when database fails  
✅ **Budget Creation**: Budgets work with local storage  

## Troubleshooting

### If you see "relation does not exist" errors:
- Make sure you ran the SQL script in the correct Supabase project
- Check that the tables were created in the Table Editor
- Verify your Supabase URL and API key are correct in `lib/main.dart`

### If you see authentication errors:
- Make sure Row Level Security (RLS) is enabled on all tables
- Verify the RLS policies were created correctly
- Check that users are properly authenticated

### If you see column name errors:
- The SQL script now uses the exact column names from your app
- Column names like `categoryId`, `startDate`, `endDate`, `isRecurring` are properly quoted
- This should resolve the "Could not find column" errors

### If dropdowns show errors:
- The app now uses local fallback when database is unavailable
- Categories will be loaded from default categories if database fails
- Transactions will be stored locally if database is not available

## Features After Setup

✅ **Cloud Sync**: All data syncs across devices  
✅ **User Isolation**: Each user only sees their own data  
✅ **Real-time Updates**: Changes appear immediately  
✅ **Offline Support**: App works even without internet  
✅ **Data Persistence**: Data survives app restarts  
✅ **Error Handling**: Graceful fallback to local storage  

## Next Steps

1. **Run the SQL script** in your Supabase project
2. **Test all features**: transactions, categories, budgets
3. **Add more categories** as needed
4. **Set up budgets** for different spending categories
5. **Monitor your spending** with the dashboard

## Support

If you encounter any issues:
1. Check the Flutter console for error messages
2. Verify your Supabase configuration
3. Ensure all tables were created successfully
4. The app will work locally even if Supabase setup fails

## Files Created

- `supabase_setup.sql` - Complete database setup script
- `SUPABASE_SETUP.md` - This instruction file
- Updated app code with better error handling and local fallbacks 