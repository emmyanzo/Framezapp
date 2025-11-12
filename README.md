
 Framez - Mobile Social Application

A modern mobile social application built with React Native (Expo) that allows users to share posts with text and images. Framez provides a clean, Instagram-inspired interface for social interaction with real-time updates and persistent authentication.

## Features

### Authentication
- **Secure Sign Up & Login**: User registration and login using Supabase Authentication
- **Persistent Sessions**: Users remain logged in after closing and reopening the app
- **Auto Profile Creation**: User profiles are automatically created upon registration

### Posts
- **Create Posts**: Share text-based posts with the community
- **Image Support**: Add images to posts (native platforms only)
- **Real-time Feed**: See new posts instantly with real-time subscriptions
- **Chronological Display**: Posts are displayed with the most recent first
- **Post Metadata**: Each post shows author name and timestamp

### Profile
- **User Profile**: View your personal information and stats
- **My Posts**: See all posts you've created in one place
- **Post Count**: Track how many posts you've shared
- **Sign Out**: Securely log out of your account

### Navigation
- **Tab Navigation**: Easy switching between Feed and Profile screens
- **Clean UI**: Instagram-inspired design with smooth animations
- **Pull to Refresh**: Refresh the feed with a pull-down gesture

## Technology Stack

### Frontend
- **Framework**: React Native with Expo SDK 54
- **Router**: Expo Router (file-based routing)
- **TypeScript**: Full type safety throughout the application
- **Icons**: Lucide React Native

### Backend
- **Backend Service**: Supabase
- **Database**: PostgreSQL (via Supabase)
- **Authentication**: Supabase Auth (email/password)
- **Real-time**: Supabase Realtime subscriptions

### State Management
- **Auth Context**: React Context API for authentication state
- **Local State**: React hooks for component state

```

## Database Schema

### Tables

#### profiles
- `id` (uuid, primary key) - References auth.users
- `email` (text) - User's email address
- `full_name` (text) - User's display name
- `avatar_url` (text, nullable) - Profile picture URL
- `created_at` (timestamptz) - Account creation date
- `updated_at` (timestamptz) - Last update date

#### posts
- `id` (uuid, primary key) - Unique post identifier
- `user_id` (uuid, foreign key) - References profiles.id
- `content` (text) - Post text content
- `image_url` (text, nullable) - Optional image URL
- `created_at` (timestamptz) - Post creation date
- `updated_at` (timestamptz) - Last update date

### Security

All tables use Row Level Security (RLS) to ensure:
- Users can only create/update/delete their own content
- All users can view public posts and profiles
- Authentication is required for creating posts

## Setup Instructions

### Prerequisites
- Node.js 18 or higher
- npm or yarn
- Expo Go app on your mobile device (for testing)

### Installation

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd framez
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Environment Variables**

   The project includes a `.env` file with Supabase credentials:
   ```
   EXPO_PUBLIC_SUPABASE_URL=<your-supabase-url>
   EXPO_PUBLIC_SUPABASE_ANON_KEY=<your-supabase-anon-key>
   ```

4. **Database Setup**

   The database schema is already configured with:
   - User profiles table
   - Posts table
   - Row Level Security policies
   - Real-time subscriptions

### Running the App

#### Development Mode
```bash
npm run dev
```

This will start the Expo development server. You can then:
- Press `w` to open in web browser
- Scan the QR code with Expo Go app (iOS/Android)
- Press `i` for iOS simulator
- Press `a` for Android emulator

#### Type Checking
```bash
npm run typecheck
```

#### Build for Web
```bash
npm run build:web
```

## Usage Guide

### Creating an Account
1. Open the app
2. Click "Sign Up" on the login screen
3. Enter your full name, email, and password
4. Click "Sign Up" to create your account
5. You'll be automatically logged in and taken to the feed

### Logging In
1. Open the app
2. Enter your email and password
3. Click "Log In"
4. You'll be taken to the feed

### Creating a Post
1. Navigate to the Feed tab
2. Tap the + button in the bottom right corner
3. Enter your post text
4. (Optional) Add an image (native platforms only)
5. Tap "Post" to share

### Viewing Your Profile
1. Navigate to the Profile tab
2. View your stats and all your posts
3. Tap "Sign Out" to log out

## Key Features Implementation

### Authentication Flow
- Root layout checks authentication state
- Unauthenticated users are redirected to login
- Authenticated users access the main app
- Sessions persist using expo-secure-store

### Real-time Updates
- Supabase Realtime subscriptions for instant updates
- Feed automatically refreshes when new posts are created
- Profile updates when user creates/deletes posts

### Data Security
- Row Level Security enforces access control
- Users can only modify their own data
- All queries are authenticated and authorized

## Platform Compatibility

### Web
- ✅ Authentication
- ✅ View posts
- ✅ Create text posts
- ❌ Image upload (requires native platform)

### iOS/Android
- ✅ Full functionality
- ✅ Image picker support
- ✅ Secure token storage
- ✅ Native performance

## Troubleshooting

### Common Issues

**Issue**: Can't log in
- **Solution**: Check that your Supabase credentials are correct in `.env`

**Issue**: Posts not showing up
- **Solution**: Pull down to refresh the feed

**Issue**: Image upload not working
- **Solution**: Image upload is only available on iOS/Android, not web

## Future Enhancements

Potential features for future development:
- Like and comment functionality
- Follow/unfollow users
- User search and discovery
- Image upload on web using Supabase Storage
- Push notifications
- Direct messaging
- Post editing and deletion
- Image filters and effects

## Demo Video

A demo video showcasing the app's functionality is available, demonstrating:
- User registration and login
- Creating posts with text and images
- Viewing the real-time feed
- Profile management
- Sign out functionality

## Appetize.io Deployment

The app is deployed on Appetize.io for easy testing without installation.


## Contact

For questions or feedback about this project, please reach out through the repository's issues section.
